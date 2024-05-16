Welcome to Navajo Nation Site Suitability Tool's documentation!
=================================================================

Access the tool here: `Navajo Nation Site Suitability Tool <https://code.earthengine.google.com/0aa00bec34930d746943f0fdcdb63065>`_

Tribal lands hold an estimated 6.5% of the total national utility-scale solar 
technical potential in the contiguous United States. Current siting practices 
typically ignore the social and cultural impacts of solar development, which 
can delay or terminate utility-scale energy projects especially if a project 
infringes on individual livelihood and local land use practices. Through early 
engagement with the tribal government of the Navajo Nation, we combined a 
Geographic Information System with a Multicriteria Decision Analysis (GIS-MCDA) 
to develop a tool to determine the relative suitability of utility-scale solar 
development on Navajo tribal lands. This serves as the documentation of this tool.

**Lumache** (/lu'make/) is a Python library for cooks and food lovers
that creates recipes mixing random ingredients.
It pulls data from the `Open Food Facts database <https://world.openfoodfacts.org/>`_
and offers a *simple* and *intuitive* API.

Check out the :doc:`Solar Siting Tool Methodology` section for further information, including
how to :ref:`Overview` the project.

Lumache has its documentation hosted on Read the Docs.

Motivation
------------

In short, the motivation is to contribute to the Navajo Nation’s goals of increasing energy access, transitioning away from fossil fuels, clean energy development, and energy sovereignty.

This tool supports the goals of the Navajo Nation. Currently, 25% of households on the Reservation lack access to electricity. The Nation has powered the Western United States for half a century. The Navajo Generating Stations, the largest coal-fired power plant in the Western US, was shut down in 2019, signaling the Nation’s intention to transition away from a coal-based economy. This year, the Navajo Nation President signed a second Executive Order 02-2023 to streamline the process to bring energy production to the Navajo Nation. Energy sovereignty, increasing clean energy development, participating in the solar and wind industry to create jobs, and paying attention to land use needs and practices are all priorities of the Tribal leadership. 


Solar Siting Tool
------------------

In short, the tool takes in different criteria and outputs a suitability score for each 30m x 30m area for how well suited that land is for a solar project. Each user as the ability to upload their own criteria and adjust the priority weights for each criteria so that inputs match their preferences.

This tool incorporates technical, environmental, and social criteria to determine a score for how well suited a specific place is for a utility-scale solar project. There are three steps to the scoring: feasibility, classification, and weighting. More information on this process can be found under the Solar Siting Tool page.


Objective
------------

This tool is not meant to be the decision maker for where to site solar projects. Instead, it is meant to provide information in the very first stage of the decision making process. When people first discuss where to site a solar project, this tool can provide preliminary information for which areas may be more suitable for others and why. For example, it can display how an area may be more or less suitable depending on whether decision makers value efficiency more or limiting impact on the local ecology.

Limitations
------------

There are three main limitations of the tool. One is the quality of the current data. All of the current data is from publicly available sources. Some are over a decade old and the correctness is not verified. The second limitation is with the omission of data. There are many criteria that we would like to consider but do not have data for — such as land designation for grazing. A user is able to upload their own data if they have it. The last limitation is because of raster analysis. The data layers all start in their own projection and resolution. In order to combine them into one analysis, they must each be adjusted to the same resolution and projection, which can cause minor issues.

.. note::

   This project is under active development.

Contents
--------

.. toctree::

   Solar Siting Tool Methodology
   api
