<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr>
<th style="text-align: center;"><strong>Common Source Amplifier
Configurations</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: left;">There are <strong>many possible design
configurations</strong> for a common source (CS) amplifier. The key
design choices revolve around what you use as the <strong>drain
load</strong> and <strong>biasing network</strong>. Here's a full
breakdown:</td>
</tr>
<tr>
<td style="text-align: center;"><img src="media/image1.png"
style="width:6.76806in;height:7.96354in" /></td>
</tr>
<tr>
<td style="text-align: center;"></td>
</tr>
<tr>
<td style="text-align: left;"><strong>What is Active Load?</strong></td>
</tr>
<tr>
<td style="text-align: left;">In MOSFET amplifier circuits, instead of a
passive resistor, the active component like a MOSFET or MOSFET circuit
(Current Mirror) is used to increase the gain of the amplifier. This
active component or the active circuit is known as the Active Load.</td>
</tr>
<tr>
<td style="text-align: left;"></td>
</tr>
<tr>
<td style="text-align: left;"><strong>Why is Active-Load used in the
circuit design?</strong></td>
</tr>
<tr>
<td style="text-align: left;">The Active Load is usually used in the
integrated circuits where the size and power consumption are major
constrain. Also, in the integrated circuits, fabricating a resistor
requires a lot of space. And therefore, instead of a resistor, the
active load is used. The active load also helps in increasing the
voltage gain of the amplifier. To understand this point, let’s take the
example of a simple common source amplifier with the passive load.</td>
</tr>
<tr>
<td style="text-align: left;"><p>The gain of the common source amplifier
is</p>
<p><span
class="math display">|<em>A</em><em>v</em>| = <em>g</em><em>m</em> * (<em>R</em><sub><em>D</em></sub> ∥ <em>r</em><sub>0</sub>) where
r<sub>0</sub>
is <em>o</em><em>u</em><em>t</em><em>p</em><em>u</em><em>t</em> <em>r</em><em>e</em><em>s</em><em>i</em><em>s</em><em>t</em><em>a</em><em>n</em><em>c</em><em>e</em> </span></p>
<p><span
class="math display"><em>I</em><em>f</em> <em>r</em><sub>0</sub> ≫ <em>R</em><sub><em>D</em></sub> <em>t</em><em>h</em><em>e</em><em>n</em> |<em>A</em><sub><em>v</em></sub>| ≈ <em>g</em><em>m</em> * <em>R</em><sub><em>D</em></sub></span></p></td>
</tr>
<tr>
<td style="text-align: left;"><p>To increase the gain, either
R<sub>D</sub> or gm needs to be increased. But as R<sub>D</sub>
increases, the voltage drop across R<sub>D</sub> also increases and
hence, the available voltage at the drain terminal reduces. At one
stage, the MOSFET may come output of the saturation.</p>
<p>Similarly, by increasing the drain current I<sub>D</sub>, the
transconductance (gm) can be increased. But as the drain current
increases, the power dissipation in the circuit increases. Also, with
the increase in the drain current, the voltage drops across the drain
resistor will increase. And at one point, MOSFET may come out of the
saturation.</p>
<p>Of course, by increasing the power supply voltage, the MOSFET can be
kept in the saturation region, and it is possible to increase the gain
by some extent. But that is not an option in the modern integrated
circuits where the supply voltage range is shrinking day by day. All
these problems can be eliminated using the active load.</p></td>
</tr>
<tr>
<td style="text-align: left;"><table style="width:99%;">
<colgroup>
<col style="width: 29%" />
<col style="width: 33%" />
<col style="width: 35%" />
</colgroup>
<thead>
<tr>
<th style="text-align: center;"><strong>Feature</strong></th>
<th style="text-align: center;"><strong>Passive (resistor)</strong></th>
<th style="text-align: center;"><strong>Active (MOSFET)</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td><em>Element type</em></td>
<td><em>Non-amplifying, dissipative</em></td>
<td><em>Has its own gm, can amplify</em></td>
</tr>
<tr>
<td><em>Small-signal impedance</em></td>
<td><em>Fixed = R<sub>D</sub></em></td>
<td><em>Very high: r<sub>o</sub> = 1/λ.I<sub>D</sub></em></td>
</tr>
<tr>
<td><em>DC voltage drop</em></td>
<td><em>Large (I<sub>D</sub>·R<sub>D</sub>)</em></td>
<td><em>Small (V<sub>DSsat</sub> ≈ 100–200mV)</em></td>
</tr>
<tr>
<td><em>Gain achievable</em></td>
<td><em>Moderate (~10–30)</em></td>
<td><em>Very high (~100–1000)</em></td>
</tr>
<tr>
<td><em>Used in</em></td>
<td><em>Discrete, RF, simple stages</em></td>
<td><em>All VLSI/IC op-amps, OTAs</em></td>
</tr>
<tr>
<td><em>Power efficiency</em></td>
<td><em>Low</em></td>
<td><em>High</em></td>
</tr>
</tbody>
</table></td>
</tr>
<tr>
<td style="text-align: left;"></td>
</tr>
</tbody>
</table>
