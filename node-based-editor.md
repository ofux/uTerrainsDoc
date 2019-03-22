# Node-Based Editor

## Introduction

If you're already familiar with the concept of a node-based editor the uTerrains Node editor will look pretty familiar.

You can open the node editor from the uTerrains Inspector by navigating to the Biomes tab and selecting Edit for either a Biome or a Biome Selector.

## Node Canvas Concepts

The background area of the window is called the "canvas". The blue and green boxes on top of the canvas are called "nodes". 

You can think of each node as representing a function. It will take some input(s) and process them into some output(s).

The little handles sticking off the sides of a node represent the function's inputs (parameters) and outputs (returns).

Different kinds of nodes will have different configurations of inputs and outputs, but the handles on the left side of a node are always its inputs and the knobs on the right of a node are its outputs. Thus, the flow of the entire graph generally runs from Left to Right.

The lines running between the nodes represent connections from the output of one node to the input of another. Each output can be connected to multiple inputs, but each input can only receive one connection.

## Node Canvas Controls

Let's go over some basic controls:
**General Navigation**
* Mouse wheel up/down to zoom in and out on the graph.
* Left-click and drag with nothing selected to pan around the canvas.
**Nodes**
* Right-click in empty space to bring up the *Create Node* menu.
* Left-click on a *node* to select that node (indicated by a slight change in the color of the node).
  * Right-click on a **selected** node to bring up the option to remove it.
  * Left-click and drag when a node is **selected** node to move it around on the canvas.
  * Left-click in an empty space to deselect a node.
**Connections**
* Left-click on an input or output handle to initiate a connection.
* Left-click the white box in the middle of a connection to delete it.
  * Left-click in empty space with an active connection to cancel the connection.
