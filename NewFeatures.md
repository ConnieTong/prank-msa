## v.140110 ##
Search order of external tools changed and bundled programs now preferred. Ancestor inference for translated alignments of DNA sequences. A fix for rare crashes due to overly long branch lengths.

<br>


<h2>v.130820</h2>
Disabled computation of alignment score for the guide tree alignment.<br>
More information about iteration with a user-provided tree.<br>
Path to other binaries no more affected by renaming of the program file.<br>
<br>
<br>


<h2>v.130708</h2>
Significant bug fixes -- update <b>strongly</b> recommended:<br>
<ul><li>option -F was mistakenly turned off by the new iterative approach<br>
</li><li>without option -F, ancestor reconstruction (and scoring) were incorrect</li></ul>

<br>


<h2>v.130410</h2>
New optimization score and iteration strategy. Ancestral character inference using maximum likelihood (BppAncestor) and output of events per tree branch. Changes in program options.<br>
<br>
<br>
<br>

<h2>v.121218</h2>
More detailed information about unmatching names. New option "-prunedata".<br>
<br>
<br>
<br>

<h2>v.121212</h2>
Support for some NHX tags. Mainly for internal usage now.<br>
<br>
<br>
<br>

<h2>v.121210</h2>
Fixed underflow errors affecting ancestral reconstruction of large alignments.<br>
<br>
<br>
<br>

<h2>v.121018</h2>
Ancestral sequences can differently indicate insertions and deletions.<br>
Can update an alignment, recomputing nodes with tag "[&&NHX:XN=realign]"<br>
<br>
<br>
<br>

<h2>v. 121002</h2>
Alignment merge now accepts trees such as "(t1:#.#,t2:#.#);". The two-node tree can be provided with "-t=filename" or "-tree=tree-string".<br>
<br>
<br>
<br>

<h2>v. 120814</h2>
Can now also merge "alignments" of one sequence.  New option <code>-mergedist=#</code> to define the distance for two alignments.<br>
<br>
<br>

<h2>v. 120717</h2>

All input data now converted to upper-case.<br>
<br>
<br>

<h2>v. 120716</h2>

Fixed the translated alignment option that had been broken in recent clean up, and corrected the output order for ancestral sequences.<br>
<br>
<br>

<h2>v. 120712</h2>

Bug fixes: the new speed-up with MAFFT often failed with codon sequence data. That has now been fixed. Also, for codon data, the guide tree is  now computed from a MAFFT alignment of translated protein sequences.<br>
<br>
<br>

<h2>v. 120626</h2>

The new version of PRANK automatically uses programs MAFFT and Exonerate to speed up the alignment. If these programs are available, the analysis starts with a quick MAFFT alignment and estimation of a NJ guide tree from that. Exonerate is used to anchor the pairwise alignments and thus massively reduce the computation time. The anchoring works for DNA, protein and codon alignments, the last one using translation to proteins in the anchoring step. The guide tree estimation and anchoring work automatically and can be disabled with options <code>-nomafft</code> and <code>-noanchors</code>, respectively.<br>
<br>
In addition to the alignment anchoring, the new version also provides an option to merge two pre-existing alignments. When merging two alignments, PRANK first infers the ancestors and the sequence at the root for each of them and then aligns the two root sequences. The new option is based on a previous (undocumented) function to finish a partially aligned alignment. See the documentation page for details.<br>
<br>
Also the previous versions of PRANK have been able to infer the ancestral sequences for a new or an existing alignment. However, the output format for this was somewhat unclear and a new option <code>-showanc</code> has now been added with a more straightforward output.<br>
<br>
Finally, the default options of the program have been slightly altered. The old behaviour and output (e.g., guide tree and xml file) can be achieved with appropriate options. See <code>prank -h</code> for details.<br>
<br>
<br>