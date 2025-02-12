# rbacon 2.3.7

* adapted source code to allow for more than 10 hiatuses/boundaries (now limited to 50)
* corrected bug causing a warning when a hiatus was set with multiple acc.mean priors provided.
* now ensures that hiatus or boundary depths are in the correct order (ascending in depth)

# rbacon 2.3.6

* further enhancements of memory usage in MCMC calculations (bacon.h)

# rbacon 2.3.5

* added function agemodel.it to extract single iterations of a Bacon age-depth model
* added functions clam2bacon and bacon2clam to translate Bacon dates files into clam files et vice versa (inspired by a suggestion from Dewey Dunnington)
* corrected behaviour of boundary and hiatus (especially if together with slumps)
* iterations with age reversals across a hiatus are now removed
* removed closeAllConnections (suggested by Dewey Dunnington)
* Added option to change the field separator to mix.curves (suggested by Thomas Dye)
* MinYr now defaults to the current year (1950 - as.integer(format(Sys.time(), "\%Y")))
* added option in the scissors function to remove a specific range of iterations (e.g., iterations 400 to 800, or the first/last 300)
* produced separate R files for groups of functions
* Bacon now stops if it finds 6 columns with unexpected names in the .csv file. If provided with a delta.R column, Bacon expects a delta.STD column as well. 
* Added an option dates.col to colour sets of dates (suggestion by Greg Cooper)
* enhancements in bacon.h of MCMC calculations and memory usage 

# rbacon 2.3.4

* faster drawing of greyscale plots (though still slower yet better than in version 2.3.1.1 and before)
* added progress bar to functions that can be slow
* repaired a bug in calculating how many dates fall within the model range
* delta.R is now accepted as a header for the dates file

# rbacon 2.3.3

* added an option to include slumps (sort of - more testing still welcome). Example: Bacon(slump=c(50, 52, 60, 70)) for two slumps between 50-52 and 60-70 cm depth
* date-files with .csv.txt extensions are now renamed to .csv (and informing us that it did so)
* default darkness of age-depth greyscale now adapts to a ratio between most and least precise sections (so that very imprecise sections still show some grey)
* repaired option depths (e.g., Bacon(depths=0:100))
* repaired height of prior distribution axes
* repaired Baconvergence()
* added a commentary after each run, mentioning the proportion of dates that lie within the age-depth model's range (some sort of 'agreement')

# rbacon 2.3.2

* Added option boundary, which sets hiatus length to (close to) 0. This leaves the hiatus functionality more or less unchanged, and should cause less confusion with setting hiatus.depths even if no hiatus is desired.
* Enhanced plotting and age calculation of depths close to hiatuses or boundaries.
* Ensured more predictable behaviour if R is started in a non-writable directory (e.g. plain, non-Rstudio R on Windows). 
* Added confidence ranges to accrate.age.ghost and accrate.depth.ghost.
* Enhanced calculation of mean and median (now based on age distribution, not on a derived histogram).
* Corrected behaviour of title.location.
* Corrected many sundry bugs related to plotting, especially with hiatuses or with BCAD=TRUE.
* Added a `NEWS.md` file to track changes to the package.

# rbacon 2.3.1.1

* Now a CRAN R package (not called bacon since that name was already taken).
* Default core directory now Bacon_runs. Other directories can be given, for more flexibility in workflows of users. 
* Calibration curves can be put in a user-specified directory ccdir (hidden by default).
* New function copyCalibrationCurve() to copy calibration curves into an R's session.
* Renamed several options to be more consistent, d.R and d.STD now named delta.R and delta.STD.
* Can now provide depths to be calculated as a variable, as alternative to using a file with depths.
* Added option to not plot x or y axis (xaxt, yaxt).
* Added option to not plot the date distributions mirrored.
* New function Baconvergence() to test for good mixing of MCMC runs. 
* Renamed weighted means of age estimates to means.
* Updated documentation.
* Renamed functions flux.age, plot.accrate.age and plot.accrate.depth to flux.age.ghost, accrate.age.ghost and accrate.depth.ghost, respectively. 
* BCAD dealt with more correctly.
* Repaired many sundry bugs.

# Bacon 2.2

* Updated to 14C calibration curves IntCal13, Marine13 and SHCal13.
* Changed .hpd to _ages.txt since many users get tricked by the extension.
* Changed from .dat files to .csv files as these are more documented and easier to open and edit by users.
* Separator for .csv file can be adapted.
* Renamed res to hopefully more intuitive thick (thickness of sections)
* Added d.R and d.STD
* Bacon.hist gives 95% ranges, mid and wmean, and reads from a file instead of from the command line. 
* Added options to change axis limits, orientation and rotation. 
* BCAD introduced, though not yet working entirely as expected.
* Different prior for acc.mean suggested if initial estimates indicate that this would be beneficial. 
* Introduced a settings file.
* removed calc.every (gave problems with long cores).
* Killed hist bug that assumed integers.
* Language cleanup of cpp files.
* Added option to remove unnecessary files after a run.
* Added option in agedepth to only plot the age-model (so not the upper panels).
* Many bug fixes in the Bacon.R and underlying C/C++ codes
