owimetadatabase API - Parametric retrieval of offshore wind turbine design data
=================================================================================

``owimetadatabase`` is a semi-structured database application used for storage of geotechnical and structural data
on offshore wind turbine structures. 

The application allow parametric retrieval of data through an Application Programming Interface (API).

This repository provides basic examples of accessing data through the API.

The database application is described in a draft journal publication submitted to Computers & Geotechnics.

Example of data retrieval are provided in the ``notebooks`` subdirectory, which contains Jupyter notebooks with example of data retrieval.

Data sources
-------------------------

Geotechnical data from the Dutch <a href="https://offshorewind.rvo.nl/">RVO sites</a> is shared under a Creative Commons licence (4.0 CC BY). 

Geotechnical data from three <a href="https://pinta.bsh.de/?lang=en">BSH sites</a> in Germany is also shared.

Public-domain data on offshore wind turbine locations and detailed monopile geometry is not available.

Obtaining access
-------------------

In order to access the data, you need to have an account and an associated API token. Contact us to obtain access (bruno.stuyts@vub.be).

API structure
---------------

Data is returned to the user in JSON format

### Location data


<table>
<thead>
  <tr>
    <th>Endpoint</th>
    <th>Description</th>
    <th>URL parameters</th>
    <th>Parameter description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><pre>/locations/projectsites/</pre></td>
    <td>Retrieves project sites</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a projectsite (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td rowspan="2"><pre>/locations/assetlocations/</pre></td>
    <td rowspan="2">Retrieves asset (wind turbine) locations</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a projectsite (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td><pre>assetlocation</pre></td>
    <td>Title of an asset location</td>
  </tr>
</tbody>
</table>

### Geotechnical data

#### Survey campaigns

<table>
<thead>
  <tr>
    <th>Endpoint</th>
    <th>Description</th>
    <th>URL parameters</th>
    <th>Parameter description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="2"><pre>/soildata/surveycampaign/</pre></td>
    <td rowspan="2">Retrieves survey campaigns</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a projectsite (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td><pre>campaign</pre></td>
    <td>Title of a survey campaign (e.g. "Borehole investigation")</td>
  </tr>
</tbody>
</table>

#### Geotechnical test locations

<table>
<thead>
  <tr>
    <th>Endpoint</th>
    <th>Description</th>
    <th>URL parameters</th>
    <th>Parameter description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="3"><pre>/soildata/testlocation/</pre></td>
    <td rowspan="3">Retrieves geotechnical test locations</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a projectsite (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td><pre>campaign</pre></td>
    <td>Title of a survey campaign (e.g. "Borehole investigation")</td>
  </tr>
  <tr>
    <td><pre>campaign</pre></td>
    <td>Title of a test location (e.g. "BH-WFS1-1")</td>
  </tr>
  <tr>
    <td rowspan="3"><pre>/soildata/testlocationproximity/</pre></td>
    <td rowspan="3">Retrieves geotechnical test locations in the proximity of a point with given coordinates</td>
    <td><pre>latitude</pre></td>
    <td>Latitude of the selected point</td>
  </tr>
  <tr>
    <td><pre>longitude</pre></td>
    <td>Longitude of the selected point</td>
  </tr>
  <tr>
    <td><pre>offset</pre></td>
    <td>Search radius in kilometer</td>
  </tr>
  <tr>
    <td rowspan="5"><pre>/soildata/testlocationprofile/</pre></td>
    <td rowspan="5">Retrieves geotechnical test locations in a band around a profile line</td>
    <td><pre>lat1</pre></td>
    <td>Latitude of the first point on the profile line</td>
  </tr>
  <tr>
    <td><pre>lon1</pre></td>
    <td>Longitude of the first point on the profile line</td>
  </tr>
  <tr>
    <td><pre>lat2</pre></td>
    <td>Latitude of the second point on the profile line</td>
  </tr>
  <tr>
    <td><pre>lon2</pre></td>
    <td>Longitude of the second point on the profile line</td>
  </tr>
  <tr>
    <td><pre>offset</pre></td>
    <td>Search band width in meters</td>
  </tr>
</tbody>
</table>

#### In-situ tests

<table>
<thead>
  <tr>
    <th>Endpoint</th>
    <th>Description</th>
    <th>URL parameters</th>
    <th>Parameter description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan><pre>/soildata/insitutesttype/</pre></td>
    <td rowspan>Retrieves in-situ test types</td>
    <td><pre>testtype</pre></td>
    <td>Title of an in-situ test type (e.g. "Seabed PCPT")</td>
  </tr>
  <tr>
    <td rowspan="5"><pre>/soildata/insitutestsummary/</pre></td>
    <td rowspan="5">Retrieves summary info on the in-situ tests (not the full data, leading to faster loading)</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a projectsite (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td><pre>campaign</pre></td>
    <td>Title of a survey campaign (e.g. "Borehole investigation")</td>
  </tr>
  <tr>
    <td><pre>location</pre></td>
    <td>Title of a test location (e.g. "BH-WFS1-1")</td>
  </tr>
  <tr>
    <td><pre>testtype</pre></td>
    <td>Title of an in-situ test type (e.g. "Seabed PCPT")</td>
  </tr>
  <tr>
    <td><pre>insitutest</pre></td>
    <td>Title of an in-situ test</td>
  </tr>
  <tr>
    <td rowspan="5"><pre>/soildata/insitutestdetail/</pre></td>
    <td rowspan="5">Retrieves detailed info on the in-situ tests (full data, leading to slower loading and possibly timeouts when retrieving too much data in one API call)</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a projectsite (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td><pre>campaign</pre></td>
    <td>Title of a survey campaign (e.g. "Borehole investigation")</td>
  </tr>
  <tr>
    <td><pre>location</pre></td>
    <td>Title of a test location (e.g. "BH-WFS1-1")</td>
  </tr>
  <tr>
    <td><pre>testtype</pre></td>
    <td>Title of an in-situ test type (e.g. "Seabed PCPT")</td>
  </tr>
  <tr>
    <td><pre>insitutest</pre></td>
    <td>Title of an in-situ test</td>
  </tr>
  <tr>
    <td rowspan="3"><pre>/soildata/insitutestproximity/</pre></td>
    <td rowspan="3">Retrieves in-situ tests in the proximity of a point with given coordinates</td>
    <td><pre>latitude</pre></td>
    <td>Latitude of the selected point</td>
  </tr>
  <tr>
    <td><pre>longitude</pre></td>
    <td>Longitude of the selected point</td>
  </tr>
  <tr>
    <td><pre>offset</pre></td>
    <td>Search radius in kilometer</td>
  </tr>
</tbody>
</table>

#### Batch lab tests

<table>
<thead>
  <tr>
    <th>Endpoint</th>
    <th>Description</th>
    <th>URL parameters</th>
    <th>Parameter description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan><pre>/soildata/batchlabtesttype/</pre></td>
    <td rowspan>Retrieves batch lab test types</td>
    <td><pre>testtype</pre></td>
    <td>Title of an batch lab test type (e.g. "Water content")</td>
  </tr>
  <tr>
    <td rowspan="5"><pre>/soildata/batchlabtestsummary/</pre></td>
    <td rowspan="5">Retrieves summary info on the batch lab tests (not the full data, leading to faster loading)</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a projectsite (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td><pre>campaign</pre></td>
    <td>Title of a survey campaign (e.g. "Borehole investigation")</td>
  </tr>
  <tr>
    <td><pre>location</pre></td>
    <td>Title of a test location (e.g. "BH-WFS1-1")</td>
  </tr>
  <tr>
    <td><pre>testtype</pre></td>
    <td>Title of an batch lab test type (e.g. "Water content")</td>
  </tr>
  <tr>
    <td><pre>batchlabtest</pre></td>
    <td>Title of a batch lab test</td>
  </tr>
  <tr>
    <td rowspan="5"><pre>/soildata/batchlabtestdetail/</pre></td>
    <td rowspan="5">Retrieves detailed info on the batch lab tests (full data, leading to slower loading and possibly timeouts when retrieving too much data in one API call)</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a projectsite (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td><pre>campaign</pre></td>
    <td>Title of a survey campaign (e.g. "Borehole investigation")</td>
  </tr>
  <tr>
    <td><pre>location</pre></td>
    <td>Title of a test location (e.g. "BH-WFS1-1")</td>
  </tr>
  <tr>
    <td><pre>testtype</pre></td>
    <td>Title of a batch lab test type (e.g. "Water content")</td>
  </tr>
  <tr>
    <td><pre>batchlabtest</pre></td>
    <td>Title of a batch lab test</td>
  </tr>
  <tr>
    <td rowspan="3"><pre>/soildata/batchlabtestproximity/</pre></td>
    <td rowspan="3">Retrieves batch lab tests in the proximity of a point with given coordinates</td>
    <td><pre>latitude</pre></td>
    <td>Latitude of the selected point</td>
  </tr>
  <tr>
    <td><pre>longitude</pre></td>
    <td>Longitude of the selected point</td>
  </tr>
  <tr>
    <td><pre>offset</pre></td>
    <td>Search radius in kilometer</td>
  </tr>
</tbody>
</table>

#### Geotechnical samples

<table>
<thead>
  <tr>
    <th>Endpoint</th>
    <th>Description</th>
    <th>URL parameters</th>
    <th>Parameter description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan><pre>/soildata/geotechnicalsampletype/</pre></td>
    <td rowspan>Retrieves sample types</td>
    <td><pre>sampletype</pre></td>
    <td>Title of a sample type (e.g. "WIP")</td>
  </tr>
  <tr>
    <td rowspan="5"><pre>/soildata/geotechnicalsample/</pre></td>
    <td rowspan="5">Retrieves summary info on the geotechnical samples</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a projectsite (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td><pre>campaign</pre></td>
    <td>Title of a survey campaign (e.g. "Borehole investigation")</td>
  </tr>
  <tr>
    <td><pre>location</pre></td>
    <td>Title of a test location (e.g. "BH-WFS1-1")</td>
  </tr>
  <tr>
    <td><pre>sampletype</pre></td>
    <td>Title of sample type (e.g. "WIP")</td>
  </tr>
  <tr>
    <td><pre>sample</pre></td>
    <td>Title of a sample</td>
  </tr>
  <tr>
    <td rowspan="3"><pre>/soildata/geotechnicalsampleproximity/</pre></td>
    <td rowspan="3">Retrieves geotechnical samples in the proximity of a point with given coordinates</td>
    <td><pre>latitude</pre></td>
    <td>Latitude of the selected point</td>
  </tr>
  <tr>
    <td><pre>longitude</pre></td>
    <td>Longitude of the selected point</td>
  </tr>
  <tr>
    <td><pre>offset</pre></td>
    <td>Search radius in kilometer</td>
  </tr>
</tbody>
</table>

#### Sample tests

<table>
<thead>
  <tr>
    <th>Endpoint</th>
    <th>Description</th>
    <th>URL parameters</th>
    <th>Parameter description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan><pre>/soildata/sampletesttype/</pre></td>
    <td rowspan>Retrieves sample test types</td>
    <td><pre>testtype</pre></td>
    <td>Title of a sample test type (e.g. "Bender element")</td>
  </tr>
  <tr>
    <td rowspan="6"><pre>/soildata/sampletestsummary/</pre></td>
    <td rowspan="6">Retrieves summary info on the sample tests (not the full data, leading to faster loading)</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a projectsite (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td><pre>campaign</pre></td>
    <td>Title of a survey campaign (e.g. "Borehole investigation")</td>
  </tr>
  <tr>
    <td><pre>location</pre></td>
    <td>Title of a test location (e.g. "BH-WFS1-1")</td>
  </tr>
  <tr>
    <td><pre>sample</pre></td>
    <td>Title of a sample (e.g. "W18")</td>
  </tr>
  <tr>
    <td><pre>testtype</pre></td>
    <td>Title of a sample test type (e.g. "Bender element")</td>
  </tr>
  <tr>
    <td><pre>sampletest</pre></td>
    <td>Title of a sample test</td>
  </tr>
  <tr>
    <td rowspan="6"><pre>/soildata/sampletestdetail/</pre></td>
    <td rowspan="6">Retrieves detailed info on the sample tests (full data, leading to slower loading and possibly timeouts when retrieving too much data in one API call)</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a projectsite (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td><pre>campaign</pre></td>
    <td>Title of a survey campaign (e.g. "Borehole investigation")</td>
  </tr>
  <tr>
    <td><pre>location</pre></td>
    <td>Title of a test location (e.g. "BH-WFS1-1")</td>
  </tr>
  <tr>
    <td><pre>sample</pre></td>
    <td>Title of a sample (e.g. "W18")</td>
  </tr>
  <tr>
    <td><pre>testtype</pre></td>
    <td>Title of a sample test type (e.g. "Bender element")</td>
  </tr>
  <tr>
    <td><pre>sampletest</pre></td>
    <td>Title of a sample test</td>
  </tr>
  <tr>
    <td rowspan="3"><pre>/soildata/sampletestproximity/</pre></td>
    <td rowspan="3">Retrieves sample tests in the proximity of a point with given coordinates</td>
    <td><pre>latitude</pre></td>
    <td>Latitude of the selected point</td>
  </tr>
  <tr>
    <td><pre>longitude</pre></td>
    <td>Longitude of the selected point</td>
  </tr>
  <tr>
    <td><pre>offset</pre></td>
    <td>Search radius in kilometer</td>
  </tr>
</tbody>
</table>

#### Soil types, soil units and soil profiles

<table>
<thead>
  <tr>
    <th>Endpoint</th>
    <th>Description</th>
    <th>URL parameters</th>
    <th>Parameter description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><pre>/soildata/soiltype/</pre></td>
    <td>Retrieves soil types</td>
    <td><pre>soiltype</pre></td>
    <td>Title of a soil type (e.g. "SAND")</td>
  </tr>
  <tr>
    <td rowspan="3"><pre>/soildata/soilunit/</pre></td>
    <td rowspan="3">Retrieves soil units</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a project site (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td><pre>soiltype</pre></td>
    <td>Title of the dominant soil type in the unit (e.g. "SAND")</td>
  </tr>
  <tr>
    <td><pre>soilunit</pre></td>
    <td>Title of a soil unit (e.g. "Borssele A - Southern Bight")</td>
  </tr>
  <tr>
    <td rowspan="3"><pre>/soildata/soilprofilesummary/</pre></td>
    <td rowspan="3">Retrieves summary information on soil profiles (not full layering and soil parameters, leading to faster loading)</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a project site (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td><pre>location</pre></td>
    <td>Title of the location (can be an AssetLocation or TestLocation) (e.g. "BH-WFS1-1")</td>
  </tr>
  <tr>
    <td><pre>soilprofile</pre></td>
    <td>Title of a soil profile (e.g. "Borehole log")</td>
  </tr>
  <tr>
    <td rowspan="3"><pre>/soildata/soilprofiledetail/</pre></td>
    <td rowspan="3">Retrieves detailed information on soil profiles (including full layering and soil parameters, leading to slower loading)</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a project site (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td><pre>location</pre></td>
    <td>Title of the location (can be an AssetLocation or TestLocation) (e.g. "BH-WFS1-1")</td>
  </tr>
  <tr>
    <td><pre>soilprofile</pre></td>
    <td>Title of a soil profile (e.g. "Borehole log")</td>
  </tr>
  <tr>
    <td rowspan="3"><pre>/soildata/soilprofileproximity/</pre></td>
    <td rowspan="3">Retrieves soil profiles in the proximity of a point with given coordinates</td>
    <td><pre>latitude</pre></td>
    <td>Latitude of the selected point</td>
  </tr>
  <tr>
    <td><pre>longitude</pre></td>
    <td>Longitude of the selected point</td>
  </tr>
  <tr>
    <td><pre>offset</pre></td>
    <td>Search radius in kilometer</td>
  </tr>
  <tr>
    <td rowspan="4"><pre>/soildata/soillayer/</pre></td>
    <td rowspan="4">Retrieves soil layers based on specified criteria, can be used to find all layers belonging to a certain soil unit</td>
    <td><pre>projectsite</pre></td>
    <td>Title of a project site (e.g. "Borssele I")</td>
  </tr>
  <tr>
    <td><pre>location</pre></td>
    <td>Title of the location (can be an AssetLocation or TestLocation) (e.g. "BH-WFS1-1")</td>
  </tr>
  <tr>
    <td><pre>soilprofile</pre></td>
    <td>Title of a soil profile (e.g. "Borehole log")</td>
  </tr>
  <tr>
    <td><pre>soilunit</pre></td>
    <td>Title of a soil unit to which the layer belongs (e.g. "Borssele A - Southern Bight")</td>
  </tr>
</tbody>
</table>

### Geometry data

Currently, there is no public domain geometry data in the database. Details on the API will be provided here if a shareable dataset is obtained. 

License and copyright
-----------------------

This work is provided under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License. Please check the license terms below and in the license file.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

  Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

  Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

  Neither the name of the software nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.
  
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.

Copyright (c) 2017-2021, OWI-lab, All rights reserved.

Disclaimer
-------------

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.