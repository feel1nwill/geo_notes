# Notes from [TRANSFORM](https://agilescientific.com/transform) wrap-up

2019-05-10 16:00, Chateau de Rosay

## Filippo: *swung website*

+ Showed simple, clean website template
+ Main advantage: Anyone can contribute via GitHub
  + Filippo to maintain for now
  + Please contribute!
  + For example, package descriptions are input as JSON files, which the website builder `hugo` uses to create html page
+ New channel on Slack: #website
+ Filippo to maintain for now

## Brendon/Rob: *Fracture package/well deviation surveys in Python*

+ First time making OS package
+ Includes CI, learned from Jo and Joergen
+ Plan to integrate many existing packages:
  + `welly`
  + `GemPY`
  + `PostGIS`
  + Several others
+ For now, called `WellPathPy`
  + Deviation surveys --> XYZ descriptions
+ Also sharing a separate workflow repo

## Brian/Miguel: *Connect striplog, welly, and GemPY*

+ Treated stratigraphic field observations as a horizontal well
+ Walk points becomes a deviation survey
+ Used:
  + `Striplog` - acts as a connector between libraries
  + `welly`
  + `GemPY`
+ Used `cuberead` to interactively edit/filter `pandas.DataFrame`s
+ Allows to take surfaces from `GemPY` to send back to `welly`, etc.

## Dieter: *Connect GemPY with SimPeg*

+ Allows to connect geologic model (`GemPy`) with CSEM modeling (`SimPeg`)
+ Discretize the geologic model
  + Allows import to `GemPy` or possibly `fatiando a terra`
+ Viz:
  + uses `vista` / `vtk` to visualize 3D volumes in the browser
    + update 2019-05-21: name is now [`pyvista`](https://github.com/pyvista/pyvista)
  + discretize function in `simPeg` framework includes a nice XYZ slice viz
    + `matplotlib` in the back
+ Reminder from Matt: hackathon team at Copenhagen 2018 connected `GemPy` to `devito`

## Alex/Matt/Jesper: *subsurface (xarray datatypes for subsurface)*

+ Alex started getting seismic into `xarray`
+ Matt started getting curve into `xarray`
+ Implementation details
  + `xarray` team suggests to use `accessors` rather than `subClass`
  + It feels a bit "non-native", but it can be done this way
+ Jesper worked on attaching units to seismic data
  + connected `pint` with `subsurface`
  + went through a long list of oil & gas units for some common use cases
  + `.set_units` and `.units_convert` methods
  + has tests

## Hallgrim/Antoine/Daniel/Diego/Ben: *HGBG*

+ 22x22 seismic samples encoded from seismic space to latent space
  + Variational auto-encoder -- could be other things
  + Wanted to find a common space where different kinds of data can be compared directly
  + Metric to graphically explore proximity
  + End goal: Be able to index data to compare across domains
+ Goals:
  + To answer question: What does this seismic section look like in the latent space?
  + Quickly check the edge cases and see if there is helpful info across domains/datatypes--clustering that can't be done explicitly with the human eye
+ Viz:
  + Using a quilt for now
  + Can go backward and forward to visualize connection between latent space and real space
  + Color sliders enable to track pieces forward and backward to/from latent space
+ Integrations
  + Took a few hours messing with slicing files -- would have been great to have Alex's segyio-to-xarray which will allow slicing on-the-fly in one line
  + This currently lives in [Dan's repo](https://github.com/esadan/HBGBES)

## Harry/Valentin/Joergen/Will/Jo: *segyio for arbitrary trace groupings*

+ Allows user-defined pre-stack sets of groups
  + Sorting, etc.
  + Easy interfaces
+ Status
  + Alpha out today or soon
  + Need some more test data
  + Update 2019-05-21: [prerelease version from @jokva!](https://pypi.org/project/segyio/1.9.0a1/)
+ Connections:
  + How does it connect to `geopandas`?
    + `shapely` + `pandas`
  + How does it connect to `xarray`? (`shapely` + `xarray`?)
    + `pangeo` people have been working on this??
  + Valentin has [notebook](https://github.com/equinor/segyio-notebooks/tree/master/notebooks/basic) for headers --> df + plotting
    + Wanting to build on this further, new notebooks for interrogating SEGY headers
    + Possibly this will work well with `cuberead` interactive SEGY headrs -- can re-write df column names interactively?

## Jo/John: *#journal continuous integration and the submission process*

+ Tested TravisCI (continuous integration) testing of journal submissions
+ This is a workflow to make sure journal articles are reproducible
+ Travis builds were struggling for article including `fenics`
+ However, the passing pipeline is working
+ Needs / to-dos:
  + Please send notebooks of potential papers so we can test them.
  + Some conversations / catch-ups: Leo, Lindsey Heagy, John Leeman
    + *swungcall*?
+ Questions:
  + Can we control rules for nbval tests? Can we make sure the rules are transparent?

## David/Joergen/Matt: *Write giant SEGY file*

+ Target size: 10 Tb. No, 11.
  + Got 2 Tb overnight
+ Got it to write file: 75 Mbps writing on laptop
+ With parallelization: scaling linearly at the moment (3x --> 185? Mbps)
+ Engineering team will be able to generate ludicrously large files for development testing, demos

## Summary thoughts on hackathon

+ David
  + It's been like the first hackathon 5 years ago, very special week
  + Thanks to Matt. Agile. Evan. Rob. Diego.
  + *swung* status quo approved -- but actually it's changing
    + Website is reflection -- shared platform with purpose.
    + Largest collection in the industry working on geocoding.
    + Widest range of knowledge about what people actually want to do.
+ Matt
  + Have a look at graphs (with circles for swung-created things from this week)
  + When you add connections, you exponentially add connectivity in the graph
  + Hence, superpowers
  + [Google album](https://photos.app.goo.gl/edSj5uigCHP1Qcy59)
