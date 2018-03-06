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



[fema-site]: https://www.fema.gov

[psds-site]: http://beachnourishment.wcu.edu
