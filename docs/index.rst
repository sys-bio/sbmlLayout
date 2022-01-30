.. SBMLLayout documentation master file, created by
   sphinx-quickstart on Mon Nov  8 14:18:50 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to SBMLLayout's documentation!
========================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   processSBML

------------
Introduction
------------

SBMLLayout can be used to edit SBML model files with layout an drender inforamtion. Users can 
import, edit or export an SBML file. This package supports SBML level 3, including layout and render. 

------------
Installation 
------------

To install SBMLLayout use

.. code-block:: python
   
   pip install SBMLLayout

-------------
Code Examples
-------------

Import, edit and write to an SBML file.

.. code-block:: python

   from SBMLDiagrams import processSBML
   import os

   dirname = "path//to"
   filename = "test.xml"

   f = open(os.path.join(dirname, filename), 'r')
   sbmlStr = f.read()
   f.close()

   df = processSBML.load(sbmlStr)

   print(df.getCompartmentPosition("compartment_id"))
   print(df.getNodeFillColor("node_id"))
   print(df.isBezierReactionType("reaction_id"))

   df.setCompartmentFillColor("compartment_id", "white", opacity = 0.5)
   df.setCompartmentBorderColor("compartment_id", [255, 255, 255])
   df.setNodeSize("node_id", [50.0, 30.0])
   df.setNodeTextFontColor("node_id", "#000000", opacity = 1.)
   df.setReactionLineThickness("reaction_id", 3.)

   sbmlStr_layout_render = df.export()

   f = open("output.xml", "w")
   f.write(sbmlStr_layout_render)
   f.close()

