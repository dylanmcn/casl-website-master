---
layout: post
title: Data Science FEMA Project
subtitle: By Dylan McNamara, Nick Rupp, and Greg Terlecky
root: {{site.baseurl}}
---

For the fall semester of 2017, two students in the new MS program in Data Science at UNCW, Nick Rupp and Greg Terlecky, are working in the CASL on a project looking into disasters.  I (and they) will periodically post updates here on their progress.

### October update
In the wake of the recent disasters Hurricanes Harvey, Irma and Maria, we are endeavoring to gain insight into the spatial and temporal dynamics of disaster events.  As a first step, we have developed a novel visualization of payments made by the Federal Emergency Management Agency ([FEMA][fema-site]) to aid victims recovering from damage suffered during hurricanes.  The geographic map shown below depicts these payouts over 12 years along the U.S. East and Gulf Coasts, where the colors indicate the magnitude of all payouts given to a county for a particular storm event.  The data for these images was aggregated from publicly available FEMA databases.

![hurricanes]({{ site.url }}assets/FEMA/movieTOT.gif){: .center-image }

### December update
Over the recent two months, we have combined two sources of data to provide insight into disaster dynamics.  The previous data from ([FEMA][fema-site]) was combined with a data set for all of the beach nourishment episodes that have occurred along the U.S. East Coast (this data can be found at the Program for the Study of Developed Shorelines [PSDS][psds-site]).  The scientific aim that drove our reasoning for combining these sources of data was to determine if beach nourishment acted as a protective mechanism against storms by reducing damage payouts.  

To answer this question, for every storm incident along an East Coast beach recorded in the FEMA payout database, we wanted to find the amount of sand that was left over from the most recent beach nourishment episode at that beach and thereafter use that as an hypothesized proxy for the level of protection from storms.  We assumed that the volume of sand placed in a beach nourishment episode decreased exponentially in time (a reasonable assumption given how the beach shoreface responds to being steepened in cross-section).  The image below shows a scatterplot of total damage suffered against volume of sand remaining from the most recent nourishment.  Each blue circle thus represents every storm event at every beach town in the U.S. East coast over the past 3 decades.  A simple minded assumption would be that the more sand that is left from the nourishment, the less damage one would see.  One look at that image - and IT AIN'T THAT SIMPLE!  There does seem to be a protective effect in nourishment, namely soon after very large nourishment events you don't find very large damage events.

![nourishment]({{ site.url }}assets/FEMA/Nourishment_results_v2.png){: .center-image }

The are almost as many caveats as data points at this stage (not really but there's enough of them to keep exploring).  Our next steps are to normalize the nourishment by town length (so we can see the nourishment cross section), to normalize the damage by town size, and hopefully to tease out storm size (ideally based on storm surge size rather than category strength).  Stay tuned.

### March update
The Data Science Team is hard at work, so expect some new data soon.  For now, we've made some plotting improvements to the plot above, using the visualization library Bokeh and the new declarative visualization software Altair.

#### Bokeh Plot
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>fema_html</title>

<link rel="stylesheet" href="https://cdn.pydata.org/bokeh/release/bokeh-0.12.14.min.css" type="text/css" />

<script type="text/javascript" src="https://cdn.pydata.org/bokeh/release/bokeh-0.12.14.min.js"></script>
<script type="text/javascript">
    Bokeh.set_log_level("info");
</script>
    </head>
    <body>

        <div class="bk-root">
            <div class="bk-plotdiv" id="028cb174-1c36-4c3e-b239-d63b0116e429"></div>
        </div>

        <script type="application/json" id="0c20906d-0249-4dab-9f43-b98694481287">
          {"f8d784ed-f24d-4900-8a3a-52254fd9d775":{"roots":{"references":[{"attributes":{"data_source":{"id":"c1c1a44b-933b-4e5e-b0c2-26282b27b19e","type":"ColumnDataSource"},"glyph":{"id":"2691711d-16e9-473f-841c-b529705d28c6","type":"Circle"},"hover_glyph":{"id":"b6cbf6e0-155d-4482-b8bb-b3a2431a33c5","type":"Circle"},"muted_glyph":null,"nonselection_glyph":{"id":"70254207-c593-4696-86ed-bd90674323f5","type":"Circle"},"selection_glyph":null,"view":{"id":"6d3c94f9-1317-461d-83ed-8fa6133aa99b","type":"CDSView"}},"id":"051d415c-e8c1-45e0-980b-fa44780925e5","type":"GlyphRenderer"},{"attributes":{"overlay":{"id":"5d8188f3-5485-468d-a3e1-196bbdc66aa2","type":"BoxAnnotation"}},"id":"d118078f-7478-49a8-9c8d-9d253d59d6c7","type":"BoxZoomTool"},{"attributes":{"dimension":1,"plot":{"id":"ffac850d-c1ce-400c-95e3-7303139866b7","subtype":"Figure","type":"Plot"},"ticker":{"id":"bd96c367-40bb-45ca-88ce-47338053be30","type":"BasicTicker"}},"id":"45a776df-758a-415a-a247-c25cfb9874af","type":"Grid"},{"attributes":{},"id":"bd96c367-40bb-45ca-88ce-47338053be30","type":"BasicTicker"},{"attributes":{"axis_label":"Total FEMA Damage Payout ($millions)","axis_line_width":{"value":3},"formatter":{"id":"3d6b60c2-aed6-49ab-8b6d-5af080b05032","type":"BasicTickFormatter"},"plot":{"id":"ffac850d-c1ce-400c-95e3-7303139866b7","subtype":"Figure","type":"Plot"},"ticker":{"id":"bd96c367-40bb-45ca-88ce-47338053be30","type":"BasicTicker"}},"id":"ef801b05-d2e8-4967-a062-6e4578bccb5c","type":"LinearAxis"},{"attributes":{},"id":"02613bfe-517b-406f-a07a-8c2cf9d61ed0","type":"BasicTicker"},{"attributes":{"axis_label":"Volume Nour Sand Remaining (x100,000 cubic yds)","axis_line_width":{"value":3},"formatter":{"id":"f77d9792-b1b9-4c93-88db-b6cffa2e1b93","type":"BasicTickFormatter"},"plot":{"id":"ffac850d-c1ce-400c-95e3-7303139866b7","subtype":"Figure","type":"Plot"},"ticker":{"id":"02613bfe-517b-406f-a07a-8c2cf9d61ed0","type":"BasicTicker"}},"id":"cfb87b2f-ea18-41d1-87f8-ef7becdb1faa","type":"LinearAxis"},{"attributes":{"plot":{"id":"ffac850d-c1ce-400c-95e3-7303139866b7","subtype":"Figure","type":"Plot"},"ticker":{"id":"02613bfe-517b-406f-a07a-8c2cf9d61ed0","type":"BasicTicker"}},"id":"19da9659-aab8-4719-8c16-824885c090f6","type":"Grid"},{"attributes":{"plot":null,"text":"Damage and Nourishment"},"id":"94cefcd9-f812-4722-911a-5d4ffc11a75f","type":"Title"},{"attributes":{},"id":"6844a19f-f287-4d30-af1c-b72dffabee50","type":"LinearScale"},{"attributes":{},"id":"cb44cc9b-7dc4-48b9-9862-4d0a25e6bec4","type":"LinearScale"},{"attributes":{},"id":"f77d9792-b1b9-4c93-88db-b6cffa2e1b93","type":"BasicTickFormatter"},{"attributes":{"callback":null},"id":"39ccb941-3bf7-4776-9535-c488ad7d6b3e","type":"DataRange1d"},{"attributes":{},"id":"3d6b60c2-aed6-49ab-8b6d-5af080b05032","type":"BasicTickFormatter"},{"attributes":{"active_drag":"auto","active_inspect":"auto","active_scroll":"auto","active_tap":"auto","tools":[{"id":"34b0403b-10fa-47f3-be02-ba746f16356d","type":"HoverTool"},{"id":"d118078f-7478-49a8-9c8d-9d253d59d6c7","type":"BoxZoomTool"},{"id":"1edb1cd8-c6ca-47b2-8c41-bdf21d817fee","type":"ResetTool"}]},"id":"e7cb9b59-d47c-4e1c-9af6-10f6efc30c60","type":"Toolbar"},{"attributes":{"bottom_units":"screen","fill_alpha":{"value":0.5},"fill_color":{"value":"lightgrey"},"left_units":"screen","level":"overlay","line_alpha":{"value":1.0},"line_color":{"value":"black"},"line_dash":[4,4],"line_width":{"value":2},"plot":null,"render_mode":"css","right_units":"screen","top_units":"screen"},"id":"5d8188f3-5485-468d-a3e1-196bbdc66aa2","type":"BoxAnnotation"},{"attributes":{"source":{"id":"c1c1a44b-933b-4e5e-b0c2-26282b27b19e","type":"ColumnDataSource"}},"id":"6d3c94f9-1317-461d-83ed-8fa6133aa99b","type":"CDSView"},{"attributes":{"below":[{"id":"cfb87b2f-ea18-41d1-87f8-ef7becdb1faa","type":"LinearAxis"}],"left":[{"id":"ef801b05-d2e8-4967-a062-6e4578bccb5c","type":"LinearAxis"}],"plot_height":400,"plot_width":400,"renderers":[{"id":"cfb87b2f-ea18-41d1-87f8-ef7becdb1faa","type":"LinearAxis"},{"id":"19da9659-aab8-4719-8c16-824885c090f6","type":"Grid"},{"id":"ef801b05-d2e8-4967-a062-6e4578bccb5c","type":"LinearAxis"},{"id":"45a776df-758a-415a-a247-c25cfb9874af","type":"Grid"},{"id":"5d8188f3-5485-468d-a3e1-196bbdc66aa2","type":"BoxAnnotation"},{"id":"051d415c-e8c1-45e0-980b-fa44780925e5","type":"GlyphRenderer"}],"title":{"id":"94cefcd9-f812-4722-911a-5d4ffc11a75f","type":"Title"},"toolbar":{"id":"e7cb9b59-d47c-4e1c-9af6-10f6efc30c60","type":"Toolbar"},"x_range":{"id":"1fd5da12-c68a-45a8-a989-90653e8d958d","type":"DataRange1d"},"x_scale":{"id":"cb44cc9b-7dc4-48b9-9862-4d0a25e6bec4","type":"LinearScale"},"y_range":{"id":"39ccb941-3bf7-4776-9535-c488ad7d6b3e","type":"DataRange1d"},"y_scale":{"id":"6844a19f-f287-4d30-af1c-b72dffabee50","type":"LinearScale"}},"id":"ffac850d-c1ce-400c-95e3-7303139866b7","subtype":"Figure","type":"Plot"},{"attributes":{"fill_alpha":{"value":0.1},"fill_color":{"value":"#1f77b4"},"line_alpha":{"value":0.1},"line_color":{"value":"#1f77b4"},"size":{"units":"screen","value":5},"x":{"field":"x"},"y":{"field":"y"}},"id":"70254207-c593-4696-86ed-bd90674323f5","type":"Circle"},{"attributes":{"callback":null},"id":"1fd5da12-c68a-45a8-a989-90653e8d958d","type":"DataRange1d"},{"attributes":{"callback":null,"column_names":["x","y","desc"],"data":{"desc":["HURRICANE IRENE","HURRICANE WILMA","HURRICANE SANDY","HURRICANE WILMA","HURRICANE SANDY","HURRICANE RITA","TROPICAL STORM FRANCES","HURRICANE IRENE","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE SANDY","HURRICANE WILMA","HURRICANE ISAAC","HURRICANE WILMA","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE SANDY","HURRICANE KATRINA","HURRICANE WILMA","HURRICANE IRENE","HURRICANE MATTHEW","HURRICANE IRENE","HURRICANE WILMA","HURRICANE IRENE","HURRICANE WILMA","HURRICANE SANDY","HURRICANE WILMA","HURRICANE FRANCES","HURRICANE WILMA","HURRICANE IRENE","HURRICANE SANDY","HURRICANE SANDY","HURRICANE FRANCES","HURRICANE FRANCES","HURRICANE SANDY","HURRICANE WILMA","HURRICANE SANDY","HURRICANE SANDY","HURRICANE SANDY","HURRICANE SANDY","HURRICANE WILMA","HURRICANE SANDY","HURRICANE IVAN","HURRICANE SANDY","HURRICANE MATTHEW","HURRICANE JEANNE","HURRICANE IRENE","TROPICAL DEPRESSION IVAN","HURRICANE IRENE","HURRICANE WILMA","HURRICANE IVAN","HURRICANE IVAN","HURRICANE SANDY","HURRICANE IVAN","HURRICANE JEANNE","HURRICANE SANDY","HURRICANE SANDY","HURRICANE FRANCES","HURRICANE WILMA","HURRICANE IVAN","HURRICANE FRANCES","HURRICANE RITA","HURRICANE IRENE","HURRICANE JEANNE","HURRICANE IVAN","HURRICANE SANDY","HURRICANE SANDY","HURRICANE WILMA","HURRICANE IRENE","HURRICANE SANDY","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE JEANNE","HURRICANE IRENE","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE FRANCES","HURRICANE JEANNE","HURRICANE SANDY","HURRICANE RITA","HURRICANE SANDY","HURRICANE SANDY","HURRICANE MATTHEW","HURRICANE WILMA","HURRICANE JEANNE","HURRICANE JEANNE","HURRICANE RITA","HURRICANE DENNIS","HURRICANE MATTHEW","HURRICANE JEANNE","HURRICANE SANDY","HURRICANE IVAN","HURRICANE ISAAC","HURRICANE MATTHEW","HURRICANE IRENE","HURRICANE DENNIS","HURRICANE SANDY","HURRICANE SANDY","HURRICANE SANDY","HURRICANE KATRINA","HURRICANE SANDY","HURRICANE MATTHEW","HURRICANE SANDY","HURRICANE KATRINA","HURRICANE SANDY","HURRICANE MATTHEW","HURRICANE MATTHEW","HURRICANE RITA","HURRICANE FRANCES","HURRICANE MATTHEW","HURRICANE FRANCES","HURRICANE RITA","HURRICANE FRANCES","HURRICANE ISAAC","HURRICANE IRENE","HURRICANE DENNIS","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE SANDY","HURRICANE IRENE","HURRICANE IRENE","HURRICANE FRANCES","HURRICANE SANDY","HURRICANE KATRINA","HURRICANE ISAAC","HURRICANE DENNIS","HURRICANE SANDY","HURRICANE JEANNE","HURRICANE JEANNE","HURRICANE IRENE","HURRICANE SANDY","HURRICANE FRANCES","HURRICANE MATTHEW","HURRICANE JEANNE","HURRICANE ISAAC","HURRICANE FRANCES","HURRICANE MATTHEW","HURRICANE JEANNE","HURRICANE IRENE","HURRICANE IVAN","HURRICANE FRANCES","HURRICANE FRANCES","HURRICANE KATRINA","HURRICANE IRENE","HURRICANE IVAN","HURRICANE IVAN","HURRICANE SANDY","HURRICANE SANDY","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE WILMA","HURRICANE SANDY","HURRICANE SANDY","HURRICANE SANDY","HURRICANE SANDY","HURRICANE WILMA","HURRICANE IVAN","HURRICANE MATTHEW","HURRICANE MATTHEW","HURRICANE IKE","HURRICANE SANDY","HURRICANE DOLLY","HURRICANE SANDY","HURRICANE SANDY","HURRICANE SANDY","HURRICANE SANDY","HURRICANE SANDY","HURRICANE KATRINA","HURRICANE IVAN","HURRICANE KATRINA","HURRICANE SANDY","HURRICANE IVAN","HURRICANE WILMA","HURRICANE WILMA","HURRICANE WILMA","HURRICANE SANDY","HURRICANE WILMA","HURRICANE RITA","HURRICANE WILMA","HURRICANE JEANNE","HURRICANE RITA","HURRICANE RITA","HURRICANE SANDY","HURRICANE WILMA","HURRICANE DENNIS","HURRICANE SANDY","HURRICANE WILMA","HURRICANE SANDY","HURRICANE IRENE","HURRICANE DENNIS","HURRICANE RITA","HURRICANE KATRINA","HURRICANE RITA","HURRICANE KATRINA","HURRICANE IVAN","HURRICANE IVAN","HURRICANE WILMA","HURRICANE KATRINA","HURRICANE KATRINA","HURRICANE RITA","HURRICANE MATTHEW","HURRICANE IKE","HURRICANE IKE","HURRICANE KATRINA","HURRICANE IRENE","HURRICANE SANDY","HURRICANE SANDY","HURRICANE MATTHEW","HURRICANE KATRINA","HURRICANE MATTHEW","HURRICANE IVAN","HURRICANE JEANNE","HURRICANE IVAN","HURRICANE IRENE","HURRICANE FRANCES","HURRICANE JEANNE","HURRICANE IRENE","HURRICANE IRENE","HURRICANE IKE","HURRICANE KATRINA","HURRICANE IVAN","HURRICANE KATRINA","HURRICANE SANDY","HURRICANE IVAN","HURRICANE KATRINA","HURRICANE IVAN","HURRICANE IVAN","HURRICANE DOLLY","HURRICANE KATRINA","HURRICANE MATTHEW","HURRICANE IVAN","HURRICANE KATRINA","HURRICANE MATTHEW","HURRICANE MATTHEW","HURRICANE ALEX","HURRICANE IKE","HURRICANE SANDY","HURRICANE SANDY","HURRICANE SANDY","HURRICANE IVAN","HURRICANE IVAN","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE KATRINA","HURRICANE KATRINA","HURRICANE SANDY","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE KATRINA","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE IRENE","HURRICANE KATRINA","HURRICANE MATTHEW","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE IRENE","HURRICANE MATTHEW","HURRICANE KATRINA","HURRICANE FRANCES","HURRICANE KATRINA","HURRICANE MATTHEW","HURRICANE JEANNE","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE DENNIS","HURRICANE KATRINA","HURRICANE KATRINA","HURRICANE FRANCES","HURRICANE DENNIS","TROPICAL STORM FRANCES","HURRICANE IVAN","HURRICANE SANDY","TROPICAL STORM FRANCES","HURRICANE KATRINA","HURRICANE SANDY","HURRICANE KATRINA","HURRICANE MATTHEW","HURRICANE KATRINA","HURRICANE KATRINA","TROPICAL STORM FRANCES","HURRICANE KATRINA","HURRICANE IKE","HURRICANE KATRINA","HURRICANE KATRINA","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE FRANCES","HURRICANE IRENE","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE MATTHEW","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE KATRINA","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE DENNIS","HURRICANE RITA","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE IKE","HURRICANE WILMA","TROPICAL STORM FRANCES","HURRICANE IRENE","HURRICANE WILMA","HURRICANE IRENE","HURRICANE IRENE","TROPICAL STORM FRANCES","HURRICANE IKE","HURRICANE MATTHEW","TROPICAL STORM FRANCES","HURRICANE MATTHEW","HURRICANE SANDY","HURRICANE MATTHEW","TROPICAL STORM FRANCES","TROPICAL STORM BONNIE AND HURRICANE CHARLEY","HURRICANE KATRINA","HURRICANE MATTHEW","HURRICANE WILMA","HURRICANE WILMA","HURRICANE SANDY","HURRICANE MATTHEW","HURRICANE WILMA","HURRICANE MATTHEW","HURRICANE WILMA","HURRICANE WILMA","HURRICANE WILMA","HURRICANE WILMA","HURRICANE IVAN","HURRICANE SANDY","HURRICANE WILMA","HURRICANE MATTHEW","HURRICANE IKE","HURRICANE DOLLY","HURRICANE KATRINA","HURRICANE WILMA","HURRICANE WILMA","HURRICANE KATRINA","HURRICANE WILMA","HURRICANE MATTHEW","HURRICANE WILMA","HURRICANE ALEX","HURRICANE WILMA","HURRICANE SANDY","HURRICANE WILMA","HURRICANE KATRINA","HURRICANE KATRINA","HURRICANE IRENE","HURRICANE SANDY","HURRICANE IKE","HURRICANE IKE","HURRICANE IRENE","HURRICANE IKE","HURRICANE WILMA","HURRICANE SANDY"],"x":{"__ndarray__":"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","dtype":"float64","shape":[344]},"y":{"__ndarray__":"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","dtype":"float64","shape":[344]}}},"id":"c1c1a44b-933b-4e5e-b0c2-26282b27b19e","type":"ColumnDataSource"},{"attributes":{"fill_color":{"value":"red"},"line_color":{"value":"red"},"size":{"units":"screen","value":5},"x":{"field":"x"},"y":{"field":"y"}},"id":"b6cbf6e0-155d-4482-b8bb-b3a2431a33c5","type":"Circle"},{"attributes":{"callback":null,"tooltips":[["(Damage,Nourish)","($x, $y)"],["Storm","@desc"]]},"id":"34b0403b-10fa-47f3-be02-ba746f16356d","type":"HoverTool"},{"attributes":{"fill_color":{"value":"#1f77b4"},"line_color":{"value":"#1f77b4"},"size":{"units":"screen","value":5},"x":{"field":"x"},"y":{"field":"y"}},"id":"2691711d-16e9-473f-841c-b529705d28c6","type":"Circle"},{"attributes":{},"id":"1edb1cd8-c6ca-47b2-8c41-bdf21d817fee","type":"ResetTool"}],"root_ids":["ffac850d-c1ce-400c-95e3-7303139866b7"]},"title":"Bokeh Application","version":"0.12.14"}}
        </script>
        <script type="text/javascript">
          (function() {
            var fn = function() {
              Bokeh.safely(function() {
                (function(root) {
                  function embed_document(root) {

                  var docs_json = document.getElementById('0c20906d-0249-4dab-9f43-b98694481287').textContent;
                  var render_items = [{"docid":"f8d784ed-f24d-4900-8a3a-52254fd9d775","elementid":"028cb174-1c36-4c3e-b239-d63b0116e429","modelid":"ffac850d-c1ce-400c-95e3-7303139866b7"}];
                  root.Bokeh.embed.embed_items(docs_json, render_items);

                  }
                  if (root.Bokeh !== undefined) {
                    embed_document(root);
                  } else {
                    var attempts = 0;
                    var timer = setInterval(function(root) {
                      if (root.Bokeh !== undefined) {
                        embed_document(root);
                        clearInterval(timer);
                      }
                      attempts++;
                      if (attempts > 100) {
                        console.log("Bokeh: ERROR: Unable to run BokehJS code because BokehJS library is missing")
                        clearInterval(timer);
                      }
                    }, 10, root)
                  }
                })(window);
              });
            };
            if (document.readyState != "loading") fn();
            else document.addEventListener("DOMContentLoaded", fn);
          })();
        </script>
    </body>
</html>

<br/>
<br/>

#### Altair Plot

<html>
<head>
  <script src="https://cdn.jsdelivr.net/npm/vega@3"></script>
  <script src="https://cdn.jsdelivr.net/npm/vega-lite@2"></script>
  <script src="https://cdn.jsdelivr.net/npm/vega-embed@3"></script>
</head>
<body>
  <div id="vis"></div>
  <script type="text/javascript">
    var spec = {
  "$schema": "https://vega.github.io/schema/vega-lite/v2.json",
  "config": {
    "view": {
      "height": 300,
      "width": 400
    }
  },
  "data": {
    "values": [
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 53837,
        "vol_left_over": 4600000
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 286329,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 3530225,
        "vol_left_over": 800000
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 997066,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 8912845,
        "vol_left_over": 272000
      },
      {
        "Title": "HURRICANE RITA",
        "totApproved": 2874,
        "vol_left_over": 0
      },
      {
        "Title": "TROPICAL STORM FRANCES",
        "totApproved": 17532,
        "vol_left_over": 747000
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 30320,
        "vol_left_over": 799504
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 1180350,
        "vol_left_over": 587746
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 405428,
        "vol_left_over": 394797
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 178623,
        "vol_left_over": 136350
      },
      {
        "Title": "HURRICANE ISAAC",
        "totApproved": 3100,
        "vol_left_over": 230000
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 5308,
        "vol_left_over": 136350
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 34640,
        "vol_left_over": 587746
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 125643,
        "vol_left_over": 96000
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 811917,
        "vol_left_over": 530729
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 178623,
        "vol_left_over": 180420
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 21383,
        "vol_left_over": 800000
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 15483,
        "vol_left_over": 130000
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 17482,
        "vol_left_over": 799504
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 961158,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 36417,
        "vol_left_over": 1003000
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 325,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 4567667,
        "vol_left_over": 800000
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 5308,
        "vol_left_over": 180420
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 121956,
        "vol_left_over": 10000
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 393460,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 16460,
        "vol_left_over": 175000
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 10293,
        "vol_left_over": 272000
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 1512,
        "vol_left_over": 96000
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 43631,
        "vol_left_over": 587746
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 86425,
        "vol_left_over": 10000
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 405428,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 694289,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 27182,
        "vol_left_over": 1250000
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 9945562,
        "vol_left_over": 1325000
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 59364,
        "vol_left_over": 450000
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 674309,
        "vol_left_over": 96000
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 107829,
        "vol_left_over": 509504
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 107749,
        "vol_left_over": 390095
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 2434,
        "vol_left_over": 606814
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 38817,
        "vol_left_over": 502789
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 15483,
        "vol_left_over": 1083597
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 11154,
        "vol_left_over": 1040253
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 7898,
        "vol_left_over": 118762
      },
      {
        "Title": "TROPICAL DEPRESSION IVAN",
        "totApproved": 921,
        "vol_left_over": 1126941
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 2532,
        "vol_left_over": 441414
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 628,
        "vol_left_over": 509504
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 530433,
        "vol_left_over": 3682757
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 2446456,
        "vol_left_over": 606814
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 928109,
        "vol_left_over": 260063
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 882533,
        "vol_left_over": 3682757
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 46208,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 8273,
        "vol_left_over": 151703
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 3741577,
        "vol_left_over": 151703
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 53207,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 1284576,
        "vol_left_over": 8668
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 10577,
        "vol_left_over": 606814
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 544291,
        "vol_left_over": 280868
      },
      {
        "Title": "HURRICANE RITA",
        "totApproved": 9200,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 21383,
        "vol_left_over": 1213629
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 122,
        "vol_left_over": 280868
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 111833,
        "vol_left_over": 606814
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 9945562,
        "vol_left_over": 869478
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 4692,
        "vol_left_over": 693502
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 3148810,
        "vol_left_over": 8668
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 48286,
        "vol_left_over": 402231
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 1939794,
        "vol_left_over": 693072
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 1394,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 365204,
        "vol_left_over": 280868
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 522,
        "vol_left_over": 402231
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 3357,
        "vol_left_over": 280868
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 151470,
        "vol_left_over": 1040253
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 109664,
        "vol_left_over": 1040253
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 3532370,
        "vol_left_over": 693502
      },
      {
        "Title": "HURRICANE RITA",
        "totApproved": 2465,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 29863,
        "vol_left_over": 693502
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 125643,
        "vol_left_over": 348685
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 11666,
        "vol_left_over": 392660
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 87812,
        "vol_left_over": 901772
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 64805,
        "vol_left_over": 864198
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 69627,
        "vol_left_over": 864198
      },
      {
        "Title": "HURRICANE RITA",
        "totApproved": 26200,
        "vol_left_over": 1277511
      },
      {
        "Title": "HURRICANE DENNIS",
        "totApproved": 54957,
        "vol_left_over": 3192500
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 21241,
        "vol_left_over": 422037
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 103737,
        "vol_left_over": 864198
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 107749,
        "vol_left_over": 375738
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 17455,
        "vol_left_over": 225443
      },
      {
        "Title": "HURRICANE ISAAC",
        "totApproved": 7500,
        "vol_left_over": 217928
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 151580,
        "vol_left_over": 976920
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 15265,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE DENNIS",
        "totApproved": 1852,
        "vol_left_over": 526034
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 405428,
        "vol_left_over": 526034
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 1512,
        "vol_left_over": 348685
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 8912845,
        "vol_left_over": 102952
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 412,
        "vol_left_over": 526034
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 3962657,
        "vol_left_over": 1502
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 967,
        "vol_left_over": 1127215
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 29863,
        "vol_left_over": 1052068
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 48071,
        "vol_left_over": 526034
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 292487,
        "vol_left_over": 2254431
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 5910,
        "vol_left_over": 71390
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 5910,
        "vol_left_over": 69887
      },
      {
        "Title": "HURRICANE RITA",
        "totApproved": 9200,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 357265,
        "vol_left_over": 864198
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 28208,
        "vol_left_over": 601181
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 544291,
        "vol_left_over": 939346
      },
      {
        "Title": "HURRICANE RITA",
        "totApproved": 64765,
        "vol_left_over": 1277511
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 2980,
        "vol_left_over": 225443
      },
      {
        "Title": "HURRICANE ISAAC",
        "totApproved": 75999,
        "vol_left_over": 217928
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 24494,
        "vol_left_over": 45088
      },
      {
        "Title": "HURRICANE DENNIS",
        "totApproved": 18729,
        "vol_left_over": 526034
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 3357,
        "vol_left_over": 939346
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 4692,
        "vol_left_over": 1052068
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 93591,
        "vol_left_over": 526034
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 48286,
        "vol_left_over": 891552
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 100228,
        "vol_left_over": 864198
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 10293,
        "vol_left_over": 102952
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 355102,
        "vol_left_over": 526034
      },
      {
        "Title": "HURRICANE ISAAC",
        "totApproved": 215559,
        "vol_left_over": 338164
      },
      {
        "Title": "HURRICANE DENNIS",
        "totApproved": 47152,
        "vol_left_over": 3192500
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 3532370,
        "vol_left_over": 1052068
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 365204,
        "vol_left_over": 939346
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 122,
        "vol_left_over": 939346
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 7898,
        "vol_left_over": 214171
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 674309,
        "vol_left_over": 348685
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 497237,
        "vol_left_over": 864198
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 4580,
        "vol_left_over": 520336
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 326541,
        "vol_left_over": 864198
      },
      {
        "Title": "HURRICANE ISAAC",
        "totApproved": 292411,
        "vol_left_over": 217928
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 199056,
        "vol_left_over": 864198
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 28208,
        "vol_left_over": 120236
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 173858,
        "vol_left_over": 864198
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 522,
        "vol_left_over": 891552
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 40543,
        "vol_left_over": 16532
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 145748,
        "vol_left_over": 864198
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 117507,
        "vol_left_over": 651439
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 811917,
        "vol_left_over": 136377
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 21383,
        "vol_left_over": 586832
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 10577,
        "vol_left_over": 1172590
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 2434,
        "vol_left_over": 1172590
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 125643,
        "vol_left_over": 772867
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 1512,
        "vol_left_over": 772867
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 2316,
        "vol_left_over": 15699
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 325,
        "vol_left_over": 749154
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 3530225,
        "vol_left_over": 39086
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 405428,
        "vol_left_over": 116064
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 405428,
        "vol_left_over": 141121
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 59364,
        "vol_left_over": 580432
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 42065,
        "vol_left_over": 195431
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 27536,
        "vol_left_over": 65143
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 15483,
        "vol_left_over": 107487
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 15483,
        "vol_left_over": 368714
      },
      {
        "Title": "HURRICANE IKE",
        "totApproved": 234496,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 196358,
        "vol_left_over": 674239
      },
      {
        "Title": "HURRICANE DOLLY",
        "totApproved": 110958,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 38817,
        "vol_left_over": 208245
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 9179,
        "vol_left_over": 320367
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 1036853,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 8912845,
        "vol_left_over": 185660
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 4950990,
        "vol_left_over": 456007
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 875331,
        "vol_left_over": 164445
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 2446456,
        "vol_left_over": 1172590
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 289764,
        "vol_left_over": 164445
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 10293,
        "vol_left_over": 185660
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 111833,
        "vol_left_over": 1172590
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 997066,
        "vol_left_over": 749154
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 961158,
        "vol_left_over": 749154
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 694289,
        "vol_left_over": 749154
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 674309,
        "vol_left_over": 772867
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 393460,
        "vol_left_over": 749154
      },
      {
        "Title": "HURRICANE RITA",
        "totApproved": 313361,
        "vol_left_over": 14331
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 286329,
        "vol_left_over": 749154
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 140092,
        "vol_left_over": 651439
      },
      {
        "Title": "HURRICANE RITA",
        "totApproved": 29421,
        "vol_left_over": 748251
      },
      {
        "Title": "HURRICANE RITA",
        "totApproved": 29421,
        "vol_left_over": 756722
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 29863,
        "vol_left_over": 508712
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 23311,
        "vol_left_over": 564718
      },
      {
        "Title": "HURRICANE DENNIS",
        "totApproved": 18729,
        "vol_left_over": 1016492
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 107749,
        "vol_left_over": 127061
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 5308,
        "vol_left_over": 13609
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 4692,
        "vol_left_over": 508712
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 2532,
        "vol_left_over": 87531
      },
      {
        "Title": "HURRICANE DENNIS",
        "totApproved": 1852,
        "vol_left_over": 1016492
      },
      {
        "Title": "HURRICANE RITA",
        "totApproved": 725,
        "vol_left_over": 82448
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 20209440,
        "vol_left_over": 56471
      },
      {
        "Title": "HURRICANE RITA",
        "totApproved": 593,
        "vol_left_over": 82448
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 412,
        "vol_left_over": 1016492
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 559012,
        "vol_left_over": 169415
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 27536,
        "vol_left_over": 33883
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 178623,
        "vol_left_over": 13609
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 7478,
        "vol_left_over": 56471
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 10527,
        "vol_left_over": 56471
      },
      {
        "Title": "HURRICANE RITA",
        "totApproved": 9200,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 5910,
        "vol_left_over": 14117
      },
      {
        "Title": "HURRICANE IKE",
        "totApproved": 155362,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE IKE",
        "totApproved": 15957,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 355102,
        "vol_left_over": 1016492
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 7898,
        "vol_left_over": 146826
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 3532370,
        "vol_left_over": 508712
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 66210,
        "vol_left_over": 349560
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 62695,
        "vol_left_over": 640390
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 48071,
        "vol_left_over": 1016492
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 46906,
        "vol_left_over": 640390
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 116299,
        "vol_left_over": 4797508
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 19490,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 19072,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 16460,
        "vol_left_over": 328971
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 8264,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 2777,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 2532,
        "vol_left_over": 23497
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 2532,
        "vol_left_over": 219804
      },
      {
        "Title": "HURRICANE IKE",
        "totApproved": 840,
        "vol_left_over": 832220
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 20209440,
        "vol_left_over": 29372
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 69003,
        "vol_left_over": 4797508
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 951847,
        "vol_left_over": 146862
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 928109,
        "vol_left_over": 430796
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 51771,
        "vol_left_over": 4797508
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 388,
        "vol_left_over": 146862
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 27536,
        "vol_left_over": 48954
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 27536,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE DOLLY",
        "totApproved": 110958,
        "vol_left_over": 170360
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 10527,
        "vol_left_over": 29372
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 35022,
        "vol_left_over": 2251891
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 40543,
        "vol_left_over": 19581
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 7478,
        "vol_left_over": 29372
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 11666,
        "vol_left_over": 391390
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 5910,
        "vol_left_over": 15665
      },
      {
        "Title": "HURRICANE ALEX",
        "totApproved": 1937,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE IKE",
        "totApproved": 155362,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 8912845,
        "vol_left_over": 127280
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 38499,
        "vol_left_over": 1076991
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 10293,
        "vol_left_over": 127280
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 128003,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 56756,
        "vol_left_over": 0
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 14948,
        "vol_left_over": 6584
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 14542,
        "vol_left_over": 6584
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 12330,
        "vol_left_over": 6584
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 29136,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 24424,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 38499,
        "vol_left_over": 236800
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 11810,
        "vol_left_over": 6584
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 22175,
        "vol_left_over": 0
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 9230,
        "vol_left_over": 6584
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 30320,
        "vol_left_over": 1014251
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 17590,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 21241,
        "vol_left_over": 331944
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 5617,
        "vol_left_over": 6584
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 17482,
        "vol_left_over": 1014251
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 15483,
        "vol_left_over": 37769
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 7582,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 12454,
        "vol_left_over": 398862
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 6716,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 5910,
        "vol_left_over": 59412
      },
      {
        "Title": "HURRICANE JEANNE",
        "totApproved": 5101,
        "vol_left_over": 398862
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 3430,
        "vol_left_over": 6584
      },
      {
        "Title": "HURRICANE DENNIS",
        "totApproved": 11013,
        "vol_left_over": 4158853
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 20209440,
        "vol_left_over": 42437
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 20209440,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 836,
        "vol_left_over": 6584
      },
      {
        "Title": "HURRICANE DENNIS",
        "totApproved": 43397,
        "vol_left_over": 4158853
      },
      {
        "Title": "TROPICAL STORM FRANCES",
        "totApproved": 36235,
        "vol_left_over": 954803
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 27536,
        "vol_left_over": 25462
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 3741577,
        "vol_left_over": 285178
      },
      {
        "Title": "TROPICAL STORM FRANCES",
        "totApproved": 18165,
        "vol_left_over": 954803
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 10527,
        "vol_left_over": 42437
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 8273,
        "vol_left_over": 285178
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 10527,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 28208,
        "vol_left_over": 216090
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 7478,
        "vol_left_over": 42437
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 7478,
        "vol_left_over": 0
      },
      {
        "Title": "TROPICAL STORM FRANCES",
        "totApproved": 597,
        "vol_left_over": 954803
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 25345993,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE IKE",
        "totApproved": 697207,
        "vol_left_over": 9336
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 23967843,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 19001829,
        "vol_left_over": 0
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 56764,
        "vol_left_over": 6584
      },
      {
        "Title": "HURRICANE FRANCES",
        "totApproved": 1086,
        "vol_left_over": 235526
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 7898,
        "vol_left_over": 93362
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 35743,
        "vol_left_over": 6584
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 4580,
        "vol_left_over": 267354
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 25420,
        "vol_left_over": 6584
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 87071,
        "vol_left_over": 0
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 21489,
        "vol_left_over": 6584
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 20286,
        "vol_left_over": 6584
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 19476,
        "vol_left_over": 6584
      },
      {
        "Title": "HURRICANE DENNIS",
        "totApproved": 25213,
        "vol_left_over": 4158853
      },
      {
        "Title": "HURRICANE RITA",
        "totApproved": 313361,
        "vol_left_over": 16974
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 18785,
        "vol_left_over": 6584
      },
      {
        "Title": "HURRICANE IKE",
        "totApproved": 32337,
        "vol_left_over": 53710
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 39368,
        "vol_left_over": 345764
      },
      {
        "Title": "TROPICAL STORM FRANCES",
        "totApproved": 36235,
        "vol_left_over": 964912
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 4455,
        "vol_left_over": 3678
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 6578,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 21383,
        "vol_left_over": 22808
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 21383,
        "vol_left_over": 588607
      },
      {
        "Title": "TROPICAL STORM FRANCES",
        "totApproved": 18165,
        "vol_left_over": 964912
      },
      {
        "Title": "HURRICANE IKE",
        "totApproved": 8164,
        "vol_left_over": 53710
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 15483,
        "vol_left_over": 32741
      },
      {
        "Title": "TROPICAL STORM FRANCES",
        "totApproved": 8802,
        "vol_left_over": 964912
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 5910,
        "vol_left_over": 36787
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 107749,
        "vol_left_over": 20969
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 5910,
        "vol_left_over": 70632
      },
      {
        "Title": "TROPICAL STORM FRANCES",
        "totApproved": 597,
        "vol_left_over": 964912
      },
      {
        "Title": "TROPICAL STORM BONNIE AND HURRICANE CHARLEY",
        "totApproved": 2316,
        "vol_left_over": 29430
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 20209440,
        "vol_left_over": 22072
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 1864205,
        "vol_left_over": 551074
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 675239,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 550953,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 292487,
        "vol_left_over": 5886
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 147639,
        "vol_left_over": 551074
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 428645,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 130473,
        "vol_left_over": 551074
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 418295,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 391908,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 361964,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 303356,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE IVAN",
        "totApproved": 27536,
        "vol_left_over": 36787
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 196358,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 209393,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 22830,
        "vol_left_over": 551074
      },
      {
        "Title": "HURRICANE IKE",
        "totApproved": 155362,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE DOLLY",
        "totApproved": 110958,
        "vol_left_over": 0
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 10527,
        "vol_left_over": 22072
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 176387,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 151404,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 7478,
        "vol_left_over": 22072
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 150738,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE MATTHEW",
        "totApproved": 6657,
        "vol_left_over": 551074
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 134817,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE ALEX",
        "totApproved": 1937,
        "vol_left_over": 128022
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 133851,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 8912845,
        "vol_left_over": 80933
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 125296,
        "vol_left_over": 5708
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 875331,
        "vol_left_over": 105856
      },
      {
        "Title": "HURRICANE KATRINA",
        "totApproved": 289764,
        "vol_left_over": 105856
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 36417,
        "vol_left_over": 1471517
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 10293,
        "vol_left_over": 80933
      },
      {
        "Title": "HURRICANE IKE",
        "totApproved": 134975,
        "vol_left_over": 487440
      },
      {
        "Title": "HURRICANE IKE",
        "totApproved": 134975,
        "vol_left_over": 492958
      },
      {
        "Title": "HURRICANE IRENE",
        "totApproved": 7898,
        "vol_left_over": 368423
      },
      {
        "Title": "HURRICANE IKE",
        "totApproved": 131568,
        "vol_left_over": 53710
      },
      {
        "Title": "HURRICANE WILMA",
        "totApproved": 32112,
        "vol_left_over": 204173
      },
      {
        "Title": "HURRICANE SANDY",
        "totApproved": 1939794,
        "vol_left_over": 879231
      }
    ]
  },
  "encoding": {
    "color": {
      "field": "Title",
      "type": "nominal"
    },
    "x": {
      "axis": {
        "title": "Volume Nour Sand Remaining (cubic yds)"
      },
      "field": "vol_left_over",
      "type": "quantitative"
    },
    "y": {
      "axis": {
        "title": "Total FEMA Damage Payout ($)"
      },
      "field": "totApproved",
      "type": "quantitative"
    }
  },
  "mark": "point",
  "selection": {
    "selector004": {
      "bind": "scales",
      "encodings": [
        "x",
        "y"
      ],
      "type": "interval"
    }
  }
};
    var opt = {"renderer": "canvas", "actions": false};
    vegaEmbed("#vis", spec, opt);
  </script>
</body>
</html>



[fema-site]: https://www.fema.gov

[psds-site]: http://beachnourishment.wcu.edu
