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

<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node1.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


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

<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node2.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


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

<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node3.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


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

<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node4.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


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

<p id="gdcalert6" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node5.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert7">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


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

<p id="gdcalert7" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node6.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert8">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/uTerrain-Node6.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Subtracts two values, using weighting as in Add mode (see above).
   </td>
  </tr>
  <tr>
   <td>Blend: Multiply
   </td>
   <td>

<p id="gdcalert8" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node7.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert9">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/uTerrain-Node7.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Multiplies two values.
   </td>
  </tr>
  <tr>
   <td>Blend: Min
   </td>
   <td>

<p id="gdcalert9" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node8.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert10">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/uTerrain-Node8.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Outputs the minimum of two values.
   </td>
  </tr>
  <tr>
   <td>Blend: Max
   </td>
   <td>

<p id="gdcalert10" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node9.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert11">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


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

<p id="gdcalert11" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node10.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert12">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/uTerrain-Node10.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Return absolute value of input.
   </td>
  </tr>
  <tr>
   <td>Clamp
   </td>
   <td>

<p id="gdcalert12" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node11.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert13">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/uTerrain-Node11.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Return input clamped to min/max range.
   </td>
  </tr>
  <tr>
   <td>Curve
   </td>
   <td>

<p id="gdcalert13" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node12.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert14">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/uTerrain-Node12.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Apply in-range to out-range, using curve, clamped within out-range)
   </td>
  </tr>
  <tr>
   <td>Invert
   </td>
   <td>

<p id="gdcalert14" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node13.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert15">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/uTerrain-Node13.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Invert value
   </td>
  </tr>
  <tr>
   <td>Lerp
   </td>
   <td>

<p id="gdcalert15" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node14.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert16">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/uTerrain-Node14.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Linearly interpolate in-range to out-range, clamped within out-range)
   </td>
  </tr>
  <tr>
   <td>Scale bias
   </td>
   <td>

<p id="gdcalert16" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node15.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert17">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/uTerrain-Node15.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Multiply input by scale, add bias
   </td>
  </tr>
  <tr>
   <td>Terrace
   </td>
   <td>

<p id="gdcalert17" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node16.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert18">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


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

<p id="gdcalert18" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node17.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert19">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/uTerrain-Node17.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Sets voxel values for current X/Z column that are positive above input * scale, negative below it.
   </td>
  </tr>
  <tr>
   <td>To Slope
   </td>
   <td>

<p id="gdcalert19" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node18.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert20">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


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

<p id="gdcalert20" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node19.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert21">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/uTerrain-Node19.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Can have multiple of these nodes. The one with the highest weight will define the biome at any X/Y/Z position.
   </td>
  </tr>
  <tr>
   <td>Voxel Type
   </td>
   <td>

<p id="gdcalert21" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node20.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert22">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/uTerrain-Node20.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Can have multiple of these nodes. The one with the highest weight will define the voxel at any X/Y/Z position.
   </td>
  </tr>
  <tr>
   <td>Final
   </td>
   <td>

<p id="gdcalert22" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node21.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert23">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


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

<p id="gdcalert23" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node22.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert24">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


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

<p id="gdcalert24" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/uTerrain-Node23.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert25">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/uTerrain-Node23.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>Feeds a constant into other nodes.
   </td>
  </tr>
</table>
