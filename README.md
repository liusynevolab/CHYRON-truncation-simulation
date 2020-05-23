# CHYRON-truncation-simulation
These scripts underlie Figure S7 of the CHYRON paper.

This runs with Python 3.7. All necessary software is included in Anaconda3. For the 
paper, everything was run on macOS HighSierra with Anaconda3 and Python2.7 installed.

Step-by-step guide for your best experience:

Download everything in this folder.

Open the file pivottable.xlsx. All insertions from our lineage tracing dataset with an
abundance greater than 0.0139% and a length of 6 bp or greater are included in the 
"all insertions" tab.

Sort the data on the all insertions tab according to the random number in Column C,
then by the well location in Column B, then take 20% of the insertions from each well,
at random onto the "random 20 percent" tab. (Some data are there as an example.)

Make a pivot table from the random 20 percent data. Example shown in the "pivot table"
tab.

Process the pivot table as shown on the "processed pivot table" tab.

Randomly order the resulting list as shown on the "truncated" tab, then truncate the 
proper proportions of insertions. For the data shown in Figure S7, 3% of insertions
should be 2 bp, 19% should be 3 bp, 17% should be 4 bp, 40% should be 5 bp, and 21%
should be 6 bp, as shown in Table S3.

Export the truncated (or full-length, for the full-length analysis) insertions from
each well to a txt file as shown in the "withlengths.sorted.txt" files included in
this repository as examples.

Run the file ins_parsing_no_umi.py with one argument: well_data.txt

(should look like this: python3 ins_parsing_no_umi.py well_data.txt)

Enter 16 for default analysis including full-length insertions.

Program runs, generates a file called darkgreenLT_percinsDict.pkl.

Run the file jaccard.py

(should look like this: python3 jaccard.py)

One window appears, default values have been placed. You can edit the length cutoff to change the minimum length required for an insertion to be included in the analysis, for example you would type "10" on the full-length insertions to produce the results shown in Figure S7a. The count cutoff should be set at 0 as the low-abundance insertions have been removed at the beginning. You can change the recovery efficency to downsample the data, but you should leave the value as "1.0" because the data have already been downsampled earlier in the pipeline. Click quit for final graph.
