---
title: "Lidar"
layout: gridlay
sitemap: false
permalink: /lidar/
---

<style>
.btn{
    margin-bottom:5px;
    padding-top:1px;
    padding-bottom:1px;
    padding-left:15px;
    padding-right:15px;
}
.jumbotron{
    padding:3%;
    padding-bottom:10px;
    padding-top:10px;
    margin-top:10px;
    margin-bottom:30px;
}
</style>

## Example of Hertfordshire lidar measurements
<div class="jumbotron">
<h4>1. Range-corrected lidar signals </h4>

The plots below show examples of 355 nm elastic backscattering signals that are received by the Hertfordshire Multi-spectral
Raman lidar system.
The x-axis is the time in the standard UTC format, and the y-axis is the atmospheric height. The measurements
were taken on the 9th October 2018 by a vertically pointing system, and the atmosphere is sampled every 7.5 m.


<p align="center">
<img src="{{ site.url }}{{ site.baseurl }}/images/lidar/telescope_40cm_counts_RCS.png" width="100%" />
</p>




<p align="center">
<img src="{{ site.url }}{{ site.baseurl }}/images/lidar/telescope_40cm_voltage_RCS.png" width="100%" />
</p>


The upper plot shows the Range-Corrected Signals (RCS) from the photon counting (PC) data, and the lower plot shows
the RCS from the analog data. The PC data can detect weak signals that are backscattered from the
atmosphere at higher altitudes, but signals from lower atmosphere often result in PC rate saturation
due to the strong intensity of backscatter. The analog data does not have the saturation issue, but has very limited
ability in detecting weak signals. For this reason, the PC and analog data are often combined in
the analysis to cover the entire dynamic range.

</div>

<div class="jumbotron">
<h4>2. Glued lidar signals </h4>

The first step of the glue technique is to determine the glue coefficients by performing a regression using simultaneously
acquired PC and analog data. The plot below shows an example of performing regression between the PC 
and analog data. The x-axis is the analog data in units of mV, and the y-axis is the PC data in units
of MHz. The coloured scatter points represent the Probability Density Function (PDF) of measured values. This plot
shows the PC data ranges from 0 to 20 MHz, and it has a good linearity with the corresponding analog data within this range.


<p align="center">
<img src="{{ site.url }}{{ site.baseurl }}/images/lidar/glue_regression_sample_slice_40cm_652.png" width="70%" />
</p>

The next step of data glue is to convert the analog data into PC data using the regression coefficients above. This conversion 
is applied to backscattered analog signals from the lower atmosphere, whilst the corresponding PC data are saturated. The plot below shows
an example of the glued signals. It can be seen that the glue signals use the PC data above 5 km as it has higher Signal-to-Noise 
Ratio (SNR), and below 5 km the scaled analog data are used as the saturation effect is clearly seen in the PC data within this
altitude range.

<p align="center">
<img src="{{ site.url }}{{ site.baseurl }}/images/lidar/glued_signals_sample_slice_20cm_1.png" width="100%" />
</p>

</div>

<div class="jumbotron">
<h4>3. Simulation of molecular backscattering. </h4>
The total backscatter signals contain both particle and molecular backscatter signals. To retrieve the particle 
backscatter and extinction coefficients, the molecular backscatter and extinction coefficients should be known
first. All the molecular density and scattering terms can be calculated from meteorological or from 
standard-atmosphere data. The figure below shows an example of simulated molecular transmission through the
atmosphere, for an upward looking ground lidar system. The atmospheric number density profile is simulated from
the <a href="https://kauai.ccmc.gsfc.nasa.gov/instantrun/msis" target="_blank">NRLMSIS Atmosphere Model</a>.

<p align="center">
<img src="{{ site.url }}{{ site.baseurl }}/images/lidar/trans.png" width="40%" />
</p>
</div>

<div class="jumbotron">
<h4>4. Vertical profile retrieval of aerosol properties. </h4>
There are different techniques that can be used to retrieve vertical profiles of aerosol properties based on backscatter signals
from ground lidar measurements. If only backscatter elastic signals are available, the Klett-Fernald (Fernald et al., 1972; Fernald, 1984; Klett, 1981, 1985)
method can be used to retrieve the vertical profiles of aerosol backscatter coefficients, and the corresponding
aerosol extinction coefficients by assuming a constant lidar ratio (LR). The figure below shows an example of 
retrieved backscattering coefficients using the Klett-Fernald method. The x-axis is the backscattering coefficient in
units of [Mm<sup>-1</sup> sr<sup>-1</sup>], and the y-axis is the height in units of m.

<p align="center">
<img src="{{ site.url }}{{ site.baseurl }}/images/lidar/backscatter_1d_retrieval_no-1.png" width="40%" />
</p>

The figure below shows the 2D time-series retrievals of backscattering coefficients. Aerosol vertical profiles are retrieved
down to 500 m as shown in the figure, as this blind point is the lowest height of the atmosphere that can be measured by the instrument.
<p align="center">
<img src="{{ site.url }}{{ site.baseurl }}/images/lidar/backscatter_2d_retrieval.png" width="100%" />
</p>

</div>

<div class="jumbotron">
<h4>References </h4>
Fernald, F. G., Herman, B. M., and Reagan, J. A.: Determination of aerosol height distributions by lidar, J. Appl. Meteorol., 11, 482–489, 1972.

Fernald, F. G.: Analysis of atmospheric lidar observations – Some comments, Appl. Optics, 23, 652–653, 1984.

Klett, J. D.: Stable analytical inversion solution for processing lidar returns, Appl. Optics, 20, 211–220, 1981.

Klett, J. D.: Lidar inversion with variable backscatter/extinction ratios, Appl. Optics, 24, 1638–1643, 1985.
</div>