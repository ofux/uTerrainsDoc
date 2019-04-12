## Nodes


## 2D Noises


<table>
  <tr>
   <td>Fast Noise 2D
   </td>
   <td>

<img src="images/uTerrain-Node0.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Generates a value for every X/Z value based on the selected noise function.
<p>
Good for generating a heightfield.
<ul>

<li>Range of values: -1 to 1
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td>Heightmap
   </td>
   <td>


<img src="images/uTerrain-Node1.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Generates a scaled [0 to 1?] value for X/Z value based on a heightmap texture.
<p>
Good for generating a heightfield.
<ul>

<li>Range of values: either 0 to 1 or -1 to 1 (needs verification)
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td>Other Noises 2D
   </td>
   <td>

<img src="images/uTerrain-Node2.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Generates a value for every X/Z value based on the selected noise function.
<p>
Good for generating a heightfield.
<ul>

<li>Range of values: usually -1 to 1, sometimes -2 to 2
</li>
</ul>
   </td>
  </tr>
</table>



## 3D Noises


<table>
  <tr>
   <td>Fast Noise 3D
   </td>
   <td>

<img src="images/uTerrain-Node3.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Generates a volume of values based on the selected noise function.
<p>
Can be used to generates "blobs in space," "floating islands," disassociated pockets of void.
<ul>

<li>Range of values: -1 to 1?
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td>Other Noises 3D
   </td>
   <td>

<img src="images/uTerrain-Node4.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Generates a volume of values based on the selected noise function.
<p>
Can be used to generates "blobs in space," "floating islands," disassociated pockets of void.
<ul>

<li>Range of values: usually -1 to 1, sometimes -2 to 2
</li>
</ul>
   </td>
  </tr>
</table>



## Combiners


<table>
  <tr>
   <td>Blend: Add
   </td>
   <td>

<img src="images/uTerrain-Node5.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Adds two values. \
 \
Weight is multiplied to in and out, so addition is more like a weighted average.
<p>
Example: if weight = 0.25, input1 = 2, input2 = 1: \
= (2 * 0.25) + (1 + 0.75) \
= .5 + .75 \
= 1.25
   </td>
  </tr>
  <tr>
   <td>Blend: Subtract
   </td>
   <td>

<img src="images/uTerrain-Node6.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Subtracts two values, using weighting as in Add mode (see above).
   </td>
  </tr>
  <tr>
   <td>Blend: Multiply
   </td>
   <td>

<img src="images/uTerrain-Node7.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Multiplies two values.
   </td>
  </tr>
  <tr>
   <td>Blend: Min
   </td>
   <td>

<img src="images/uTerrain-Node8.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Outputs the minimum of two values.
   </td>
  </tr>
  <tr>
   <td>Blend: Max
   </td>
   <td>

<img src="images/uTerrain-Node9.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Outputs the maximum of two values.
   </td>
  </tr>
</table>



## Filters


<table>
  <tr>
   <td>Abs
   </td>
   <td>

<img src="images/uTerrain-Node10.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Return absolute value of input.
   </td>
  </tr>
  <tr>
   <td>Clamp
   </td>
   <td>


<img src="images/uTerrain-Node11.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Return input clamped to min/max range.
   </td>
  </tr>
  <tr>
   <td>Curve
   </td>
   <td>

<img src="images/uTerrain-Node12.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Apply in-range to out-range, using curve, clamped within out-range)
   </td>
  </tr>
  <tr>
   <td>Invert
   </td>
   <td>

<img src="images/uTerrain-Node13.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Invert value
   </td>
  </tr>
  <tr>
   <td>Lerp
   </td>
   <td>

<img src="images/uTerrain-Node14.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Linearly interpolate in-range to out-range, clamped within out-range)
   </td>
  </tr>
  <tr>
   <td>Scale bias
   </td>
   <td>

<img src="images/uTerrain-Node15.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Multiply input by scale, add bias
   </td>
  </tr>
  <tr>
   <td>Terrace
   </td>
   <td>

<img src="images/uTerrain-Node16.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Reduce values to a set of terrace values, of a defined width.
<p>
Width is dynamic: width (constant width) * input_width
   </td>
  </tr>
</table>



## Transformers


<table>
  <tr>
   <td>To Height
   </td>
   <td>

<img src="images/uTerrain-Node17.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Sets voxel values for current X/Z column that are positive above input * scale, negative below it.
   </td>
  </tr>
  <tr>
   <td>To Slope
   </td>
   <td>

<img src="images/uTerrain-Node18.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Returns steepness at location. \
0 = level ground, higher numbers = steeper
   </td>
  </tr>
</table>



## Final


<table>
  <tr>
   <td>Biome Selection
   </td>
   <td>

<img src="images/uTerrain-Node19.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Can have multiple of these nodes. The one with the highest weight will define the biome at any X/Y/Z position.
   </td>
  </tr>
  <tr>
   <td>Voxel Type
   </td>
   <td>

<img src="images/uTerrain-Node20.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Can have multiple of these nodes. The one with the highest weight will define the voxel at any X/Y/Z position.
   </td>
  </tr>
  <tr>
   <td>Final
   </td>
   <td>

<img src="images/uTerrain-Node21.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Receives voxel value (distance from surface, negative is underground)
   </td>
  </tr>
</table>



## Position


<table>
  <tr>
   <td>X | Y | Z
   </td>
   <td>

<img src="images/uTerrain-Node22.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Feeds a single dimension of the current location into other nodes.
   </td>
  </tr>
</table>



## Constant


<table>
  <tr>
   <td>Constant
   </td>
   <td>

<img src="images/uTerrain-Node23.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Feeds a constant into other nodes.
   </td>
  </tr>
</table>
