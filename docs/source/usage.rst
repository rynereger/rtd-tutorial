Usage
=====

.. _installation:

Overview
------------

The tool takes in social, environmental, and technical criteria as GIS raster data layers. It exists in Google Earth Engine. The current setup includes six criteria: solar radiation, slope, ecological sensitivity, distance to water, distance to roads, and distance to transmission lines. 

A score is determined for each 30m by 30m area. There are three parts to the scoring: feasibility, classification, and weighting, which will be explained below. The output is a suitability score for each 30m by 30m area. 

To use Lumache, first install it using pip:

.. code-block:: console

   (.venv) $ pip install lumache

Feasibility
----------------

The first step is to determine the constraint for each criteria. For example, we may deem that anything in a high ecologically sensitive area is not suitable to have a solar project. Another example is that anything farther than 3 miles from a transmission line is infeasible for a solar project. This now reduces the region to what is feasible and what is not.

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']

Classification
----------------

The second step is classification. For each criterion/layer, bucket the range of values into scores. This allows us to show that some areas are more preferable than others. For example, being closer to a transmission line is more preferable than being farther away. Being in a low ecologically sensitive area is more preferable than being in a highly sensitive area.

We created three buckets for each layer to represent high, medium, and low suitability. High suitability receives a score of 3, medium a 2, and low a 1. For example, being within 1 mile of a transmission line is highly preferable and receives a score of 3. Being within 1-2 miles of a transmission line is somewhat preferable and receives a score of 2. Being 2-3 miles away from a transmission line is not preferable but is still feasible and receives a score of 1. This classification is done for each layer.

Weighting
----------------

The final element of scoring is weighting. Each criteria gets a “weight” and all the weights must add up to 1. This is how we show that some criteria are more important than others. For example, it may be very important to be near a transmission line but less important to be on a low slope. Then, we can assign a higher weight to the transmission line criteria and a lower weight to score. The user must assign a weight to each layer to indicate their preference and these weights must add up to one.

Raster Overlay
----------------

Finally, the score is determined through a raster overlay. For each 30m by 30m area, there is a classification score. Let’s say that a specific area has a 3 for solar, 2 for slope, 1 for ecological sensitivity, 2 for distance to roads, and a 3 for distance to transmission lines. There is a weight for each criteria. Let’s say the weight is 0.4 for solar, 0.2 for slope, 0.1 for ecological sensitivity, 0.1 for distance to roads, and 0.2 for distance to transmission lines. Notice that the weights add to 1: 0.4+0.2+0.1+0.1+0.2 = 1. The score calculation is as follows: (solar_weight)(solar_classification) + (slope_weight)(solar_classification) + (ecol_weight)(ecol_classification) + (roads_weight)(roads_classification) + (transmission_weight)(transmission_classification) = 3 * 0.4 + 2 * 0.2 + 1 * 0.1 + 2 * 0.1 + 3 * 0.2 = 2.5 so the suitability score at this 30m by 30m area is 2.5
