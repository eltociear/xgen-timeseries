---
html_theme.sidebar_secondary.remove:
sd_hide_title: true
---

<!-- CSS overrides on the homepage only -->
<style>
.bd-main .bd-content .bd-article-container {
  max-width: 70rem; /* Make homepage a little wider instead of 60em */
}
/* Extra top/bottom padding to the sections */
article.bd-article section {
  padding: 3rem 0 7rem;
}
/* Override all h1 headers except for the hidden ones */
h1:not(.sd-d-none) {
  font-weight: bold;
  font-size: 48px;
  text-align: center;
  margin-bottom: 4rem;
}

/* Override all h3 headers that are not in hero */
h3:not(#hero h3) {
  font-weight: bold;
  text-align: center;
}
</style>

(homepage)=
# XGenTS: Exploratory analysis of Energy models

<div id="hero">

<div id="hero-left">  <!-- Start Hero Left -->
  <h2 style="font-size: 50px; font-weight: bold; margin: 2rem auto 0;">XGen Time Series</h2>
  <h3 style="font-weight: bold; margin-top: 0;">An eXplainable framework for Generative Time Series</h3>
  <p>
  Designed to improve the performance of existing models using generated data. It generates novel datasets based on past or current real-world data, enabling the model to learn and improve from this valuable additional information. XGenTS also serves as an archive for a wide range of energy-related datasets. <br> 
  It's based on PyTorch and can be installed using pip.
	  
  </p>

<div class="homepage-button-container">
  <div class="homepage-button-container-row">
      <a href="./getting_started/index.html" class="homepage-button primary-button">Get Started</a>
      <a href="./archive/index.html" class="homepage-button secondary-button">Archive</a>
      <a href="https://colab.research.google.com/github/XgenTimeSeries/xgen-timeseries/blob/master/tutorials/PSA_GAN_in_XGenTimeSeries.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>
  </div>
  <div class="homepage-button-container-row">
      <a href="./archive/" class="homepage-button-link">See Archive Reference <svg class="svg-icon" viewBox="0 0 20 20"> <path fill="none" d="M1.729,9.212h14.656l-4.184-4.184c-0.307-0.306-0.307-0.801,0-1.107c0.305-0.306,0.801-0.306,1.106,0
	l5.481,5.482c0.018,0.014,0.037,0.019,0.053,0.034c0.181,0.181,0.242,0.425,0.209,0.66c-0.004,0.038-0.012,0.071-0.021,0.109
	c-0.028,0.098-0.075,0.188-0.143,0.271c-0.021,0.026-0.021,0.061-0.045,0.085c-0.015,0.016-0.034,0.02-0.051,0.033l-5.483,5.483
	c-0.306,0.307-0.802,0.307-1.106,0c-0.307-0.305-0.307-0.801,0-1.105l4.184-4.185H1.729c-0.436,0-0.788-0.353-0.788-0.788
	S1.293,9.212,1.729,9.212z"></path></svg></a>
  </div>
</div>
</div>  <!-- End Hero Left -->

<div id="hero-right">  <!-- Start Hero Right -->

::::::{grid} 1 2 2 2
:gutter: 2

:::::{grid-item-card}
:link: example_plot_trace_bars
:link-type: ref
:shadow: none
:class-card: example-gallery

:::{div} example-img-plot-overlay
Analysis bottelneck Generative model `model.explain()`
:::

:::{image} _static/images/generative.png
:::
:::::

:::::{grid-item-card}
:link: example_plot_forest_mixed
:link-type: ref
:shadow: none
:class-card: example-gallery

:::{div} example-img-plot-overlay
Energy and electric mobility dataset `XGenTS.dataset('streaming')`
:::

:::{image} _static/images/archive.png
:::
:::::
::::::

<!-- grid ended above, do not put anything on the right of markdown closings -->

</div>  <!-- End Hero Right -->
</div>  <!-- End Hero -->


### XGen Time Series ```Archive```

<table id="customers">
  <thead>
    <tr>
      <th>Dataset</th>
      <th>Frequency</th>
      <th>Duration</th>
      <th>Type</th>
      <th>Location</th>
      <th>Measurements</th>
      <th>Download <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-download" viewBox="0 0 16 16"> <path d="M.5 9.9a.5.5 0 0 1 .5.5v2.5a1 1 0 0 0 1 1h12a1 1 0 0 0 1-1v-2.5a.5.5 0 0 1 1 0v2.5a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2v-2.5a.5.5 0 0 1 .5-.5z"></path> <path d="M7.646 11.854a.5.5 0 0 0 .708 0l3-3a.5.5 0 0 0-.708-.708L8.5 10.293V1.5a.5.5 0 0 0-1 0v8.793L5.354 8.146a.5.5 0 1 0-.708.708l3 3z"></path> </svg> </th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>XGenTS-ESS(Ours)</td>
      <td>1Hz</td>
      <td>6 month</td>
      <td>Residential</td>
      <td>France</td>
      <td>I,V, P,Q, S</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://xgentimeseries.github.io/xgen-timeseries/ess_datasets/index.html" target="_blank"> [1]</a> </td>
    </tr>
    <tr>
      <td>IDEAL</td>
      <td>1Hz</td>
      <td>18 month</td>
      <td>Residential</td>
      <td>UK</td>
      <td>P, S</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://datashare.ed.ac.uk/handle/10283/3647" target="_blank"> [2]</a> </td>
    </tr>
    <tr>
      <td>Enertalk</td>
      <td>15 Hz</td>
      <td>3 day</td>
      <td>Residential</td>
      <td>South Korea</td>
      <td>P,Q</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://www.nature.com/articles/s41597-019-0212-5" target="_blank"> [3]</a> </td>
    </tr>
    <tr>
      <td>LIT</td>
      <td>15 kHz</td>
      <td>30 sec</td>
      <td>Residential</td>
      <td>Brazil</td>
      <td>P, S</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://pessoal.dainf.ct.utfpr.edu.br/douglasrenaux/LIT_Dataset/" target="_blank"> [4]</a> </td>
    </tr>
    <tr>
      <td>AMPds</td>
      <td>0.1 mHz</td>
      <td>2 years</td>
      <td>Residential</td>
      <td>Canada</td>
      <td>P, S,I</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="http://ampds.org/" target="_blank"> [5]</a> </td>
    </tr>
    <tr>
      <td>COOLL</td>
      <td>100 kHz</td>
      <td>6 sec</td>
      <td>Individual appliance</td>
      <td>France</td>
      <td>I,V</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://coolldataset.github.io/" target="_blank"> [6]</a> </td>
    </tr>
    <tr>
      <td>WHITED</td>
      <td>44 kHz</td>
      <td>5 sec</td>
      <td>Individual appliance</td>
      <td>Multiples</td>
      <td>I</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://www.cs.cit.tum.de/dis/resources/whited/" target="_blank"> [7]</a> </td>
    </tr>
    <tr>
      <td>REFIT</td>
      <td>1 Hz</td>
      <td>4+ years</td>
      <td>Residential</td>
      <td>US</td>
      <td>P</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://pureportal.strath.ac.uk/en/datasets/refit-electrical-load-measurements-cleaned" target="_blank"> [8]</a> </td>
    </tr>
    <tr>
      <td>Dataport</td>
      <td>1 Hz</td>
      <td>4+ years</td>
      <td>Residential</td>
      <td>US</td>
      <td>P,S</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://ieee-dataport.org/" target="_blank"> [9]</a> </td>
    </tr>
    <tr>
      <td>UK-DALE</td>
      <td>16 kHz</td>
      <td>2 years</td>
      <td>Residential</td>
      <td>UK</td>
      <td>I,V, P,Q, S</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://www.nature.com/articles/sdata20157" target="_blank"> [10]</a> </td>
    </tr>
    <tr>
      <td>DRED</td>
      <td>1 Hz</td>
      <td>6 month</td>
      <td>Residential</td>
      <td>Netherlands</td>
      <td>P</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://www.st.ewi.tudelft.nl/~akshay/dred/" target="_blank"> [11]</a> </td>
    </tr>
    <tr>
      <td>PLAID</td>
      <td>30 kHz</td>
      <td>5 sec</td>
      <td>Individual appliance</td>
      <td>US</td>
      <td>I,V</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://energy.duke.edu/content/plug-load-appliance-identification-dataset-plaid" target="_blank"> [12]</a> </td>
    </tr>
     <tr>
      <td>ECO</td>
      <td>1227 kHz</td>
      <td>6 sec</td>
      <td>Residential</td>
      <td>Switzerland</td>
      <td>I,V, P, pf</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://sites.google.com/view/activities-prediction-202b/project-homepage/eco-dataset" target="_blank"> [13]</a> </td>
    </tr>
     <tr>
      <td>iAWE</td>
      <td>1 Hz</td>
      <td>73 day</td>
      <td>Residential</td>
      <td>India</td>
      <td>I, V, P, Q, S, pf</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://iawe.github.io/" target="_blank"> [14]</a> </td>
    </tr>
     <tr>
      <td>Tracebase</td>
      <td>1 Hz</td>
      <td>1 day</td>
      <td>Individual appliance</td>
      <td>Germany</td>
      <td>P</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://github.com/areinhardt/tracebase" target="_blank"> [15]</a> </td>
    </tr>
     <tr>
      <td>REDD</td>
      <td>16.5 kHz</td>
      <td>19 day</td>
      <td>Residential</td>
      <td>US</td>
      <td>I, V, P</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://tokhub.github.io/dbecd/links/redd.html" target="_blank"> [16]</a> </td>
    </tr>
     <tr>
      <td>BLUED</td>
      <td>12 kHz</td>
      <td>1 week</td>
      <td>Residential</td>
      <td>US</td>
      <td>I,V</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td><a href="https://tokhub.github.io/dbecd/links/Blued.html" target="_blank"> [17]</a> </td>
    </tr>
     <tr>
      <td>Electricity AP</td>
      <td>16mHz</td>
      <td>4 month</td>
      <td>Residential</td>
      <td>Belgium</td>
      <td>P</td>
      <td><a href="https://github.com/oublalkhalid/XGen/raw/main/_static/XGenTS-001145324.hdf5">HDF5 file</a></td>
      <td> <a href="https://opennetzero.org/dataset/electricity-maps" target="_blank"> [18]</a> </td>
    </tr>
  </tbody>
</table>


## Sponsors and Institutional Partners
<p style="font-weight: bold; margin-top: 0;"> With gratitude to <a href="https://www.ip-paris.fr/">Institute Polytechnique de Paris</a>, <a href="https://www.ox.ac.uk/">Oxford Institute of Mathematics</a>, OneTech TotalEnergies for generously supporting the development and maintenance of XGen Time Series.</p>
  
This work is licensed under a
[Creative Commons Attribution 4.0 International License][cc-by].

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png


<!-- ::::{grid} 1 3 3 3
:::{grid-item}
[![oxford_uni_logo](_static/sponsor_oxford.png)](https://www.ox.ac.uk/)
:::
:::{grid-item}
[![plytechnique_uni_logo](_static/sponsor_polytechnique.png)](https://www.ip-paris.fr/)
:::
:::: -->


:::{toctree}
:maxdepth: 1
:hidden:

Getting Started<getting_started/index>
XGenTS Archive<archive/index>
ESS dataset<ess_datasets/index>
<!-- API Reference<api/index> -->
Community <community>
Contributing<contributing/index>
About us<about>
:::
