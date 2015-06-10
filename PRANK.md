<img src='http://wiki.prank-msa.googlecode.com/git/images/prank_logo.png'>

<br>

PRANK is a probabilistic multiple alignment program for DNA, codon and amino-acid sequences. It's based on a novel algorithm that treats insertions correctly and avoids over-estimation of the number of deletion events. In addition, PRANK borrows ideas from maximum likelihood methods used in phylogenetics and correctly takes into account the evolutionary distances between sequences. Lastly, PRANK allows for defining a potential structure for sequences to be aligned and then, simultaneously with the alignment, predicts the locations of structural units in the sequences.<br>
<br>
PRANK was developed in <a href='http://www.ebi.ac.uk/goldman/'>Nick Goldman's group</a> at the EMBL-European Bioinfomatics Institute, UK, and continues now in <a href='http://blogs.helsinki.fi/sa-at-bi'>Ari Löytynoja's group</a> at the Institute of Biotechnology, University of Helsinki, Finland. These pages are meant to explain how to install and use PRANK. While they are still incomplete, more detailed information of the method may be found from the program's old home pages at <a href='http://www.ebi.ac.uk/goldman-srv/prank/'>http://www.ebi.ac.uk/goldman-srv/prank/</a>. If you have questions about PRANK, please contact me at <a href='mailto:ari.loytynoja@helsinki.fi?Subject=Question%20about%20PRANK'>ari.loytynoja@helsinki.fi</a>.<br>
<br>
<br>

<hr />
<br>

<ul><li><b><a href='http://code.google.com/p/prank-msa/wiki/PRANK?tm=6#Using_PRANK'>Using PRANK</a></b>
</li></ul><blockquote>Instructions for the use of PRANK with example commands and test data.</blockquote>

<ul><li><b><a href='http://code.google.com/p/prank-msa/wiki/InstallationInstructions?tm=6'>Installation instructions</a></b>
</li></ul><blockquote>Instructions to install and start using PRANK on different operating systems. Pre-compiled executables are provided for Windows, Mac OSX and Linux; the source code should compile on any system supporting the GNU C compiler package</blockquote>

<ul><li><b><a href='http://code.google.com/p/prank-msa/wiki/NewFeatures?tm=6'>New features</a></b>
</li></ul><blockquote>Brief description of the new features in the latest versions of the program</blockquote>

<ul><li><b><a href='http://code.google.com/p/prank-msa/wiki/PreviouslyAsked?tm=6'>Previously asked questions</a></b>
</li></ul><blockquote>Some questions previously asked by other users -- check here before contacting me</blockquote>

<ul><li><b><a href='http://code.google.com/p/prank-msa/wiki/HSAML?tm=6'>HSAML format</a></b>
</li></ul><blockquote>Definition of the XML-format used by PRANK</blockquote>

<br>

<hr />

<h1>Using PRANK</h1>


At the simplest, PRANK can be run with command:<br>
<pre><code>prank input_file<br>
</code></pre>
where <code>input_file</code> contains sequences in FASTA format.<br>
<br>
See below for the description of the most central program options.<br>
<br>
<br>

<br>
<br>
<br>

<h1>About PRANK alignments</h1>

PRANK aims at an evolutionarily correct alignment and the alignments inferred with PRANK can be expected to look different from ones generated with other alignment methods. There are, however, cases where the different look is caused by violations of the method's assumptions. To understand why things may go wrong and how to avoid that, read this <a href='http://code.google.com/p/prank-msa/wiki/ExplanationDifferences?tm=6'>explanation of differences</a> between PRANK and traditional progressive alignment methods.<br>
<br>
The reconstruction of evolutionary homology -- including the correct placement of insertion and deletion events -- is only feasible for rather closely-related sequences. PRANK is not meant for the alignment of very diverged sequences. If sequences are very different, the correct homology cannot be reconstructed with confidence and PRANK may simply refuse to match them. There are several methods developed for structural matching of very distant protein sequences. One should not consider the resulting alignment a proper inference of evolutionary homology, though.<br>
<br>
Often there are ties in the alignment, i.e. positions with many equally good solutions. The common practice among sequence aligners is always to pick the same solution among many different ones and produce consistent alignments. We believe that this gives the user a wrong impression and too high confidence on the resulting alignment (for example, 10 iterations of the alignment always produce the same result -> the alignment must be correct). Our decision is to break the ties randomly. This means that different runs of the program with the same data may give different alignments and PRANK alignment may not be reproducible. However, the practice we have chosen also tells the user that the regions not consistently aligned in a similar manner simply cannot be resolved reliably. Be aware that the reproducability in many other methods does not mean higher confidence -- they also reproduce exactly the same errors!<br>
<br>
<br>
<br>
<BR><br>
<br>
<br>
<br>
<h1>Main program options</h1>

A typical command for PRANK could be:<br>
<pre><code>prank -d=input_file -t=tree_file -o=output_file -F<br>
</code></pre>
Here, <code>input_file</code> is the name of the file with input sequences in FASTA format, <code>tree_file</code> is the name of the file with a phylogeny with branch lengths relating these sequences, and <code>output_file</code> is the name of the file (with extension <code>.best.fas</code>) where the resulting alignment will be written in FASTA format; <code>-F</code> specifies that the inference of insertions should be trusted and sites appearing as insertions should not be aligned at the later stages of the process.<br>
<br>
Of these parameters, only <code>-d=input_file</code> is strictly required (and, when given alone, can be given in the form <code>prank input_file</code>). If the option <code>-t=tree_file</code> is omitted, an alignment guide tree is inferred from the input data (see below). If the option <code>-o=output_file</code> is omitted, the results are written to file named <code>output.best.fas</code>. Finally, if option <code>-F</code> is omitted, the algorithm does not incorrectly penalise for gaps for insertions but it will also not guarantee to leave the insertions unmatched.<br>
<br>
By default, PRANK iterates the alignment five times, inferring a new guide tree after each alignment. For each solution, it computes a phylogeny-aware alignments score and, after the full analysis, outputs the best-scoring solution. The number of iterations performed can be changed with option <code>-iterate=#</code> and the iteration completely disabled with option <code>-once</code>. See <a href='http://code.google.com/p/prank-msa/wiki/PRANK?tm=6#Methods'>Methods</a> for more details.<br>
<br>
Without additional options, PRANK outputs only the alignment. More information can be outputted with the following options:<br>
<br>
<code>-showtree</code>: output the guide tree used<br>
<code>-showxml</code>: output the results in PRANK's own XML format<br>
<code>-showanc</code>: output ancestral sequences and guide tree<br>
<code>-showevents</code>: output events per branch<br>
<code>-showall</code>: output all listed above<br>
<code>-showiter</code>: output results for each iteration<br>
<br>
If a guide tree is provided, PRANK assumes that the sequence names in the tree and data file match exactly. Special characters and white spaces in the names may cause problems and may have to be removed/replaced with underscores. With option <code>-shortnames</code> only the first part (until the first white space) of the names in the data file are matched against the names in the guide tree. Extra names in the guide tree/data file can be removed with options <code>-prunetree</code> and <code>-prunedata</code>.<br>
<br>
A list of possible program options is shown with command:<br>
<pre><code>prank -help <br>
</code></pre>

By default, PRANK writes the output alignments in FASTA format. With the option <code>-f=format_name</code> some other popular formats can be selected. See <code>prank -help</code> for details.<br>
<br>
<br>
<br>
<br>
<BR><br>
<br>
<br>
<h1>Other program options</h1>

<h2>Translated alignment and codon alignment</h2>

PRANK can do translated alignments of protein-coding DNA sequences or align them using the codon model. Translation is selected with the options <code>-translate</code> (standard code) or <code>-mttranslate</code> (mitochondrial code), and the codon alignment with the option <code>-codon</code>.  Using the example data <a href='http://wiki.prank-msa.googlecode.com/git/data/input_dna.fas'>input_dna.fas</a>, the following commands make a translated alignment:<br>
<pre><code>prank -d=input_dna.fas -o=output_translated -translate -F<br>
</code></pre>
and a codon alignment:<br>
<pre><code>prank -d=input_dna.fas -o=output_codon -codon -F<br>
</code></pre>

See <a href='http://code.google.com/p/prank-msa/wiki/PRANK?tm=6#Methods'>Methods</a> for more details.<br>
<br>
<br>
<br>
<BR><br>
<br>
<br>
<br>
<h2>Inference of ancestral sequences and ancestral events</h2>

The key aim of the phylogeny-aware alignment algorithm is to correctly model the insertion and deletion events and accurately infer the ancestral sequences, especially the presence and absence of characters. The ancestral sequences, that PRANK internally will anyway infer, can be of great interest and can also be outputted. The earlier output format for the ancestral sequences was not clear and new option <code>-showanc</code> has been added. This option now inserts the ancestral sequences in the position they appear in the alignment tree structure and, when viewed together with a phylogenetic tree with internal nodes labelled accordingly, make it easy to assign evolutionary events to specific tree branches. The two output files are named <code>*.best.anc.fas</code> and <code>*.best.anc.dnd</code>; with the option <code>-showevents</code>, the inferred events are listed per branch and outputted to file <code>*.best.events</code>.<br>
<br>
Ancestral sequences can be outputted for alignments generated with PRANK but they can also be inferred for existing alignments. While PRANK by default removes all the gap characters in the input data, this can be disabled with option <code>-keep</code> and it then reads the alignment as it is. Thus with command:<br>
<pre><code>prank -d=alignment_pep.fas -showanc -showevents -keep -o=output_ancestors -njtree [OR -t=treefile]<br>
</code></pre>
PRANK will infer the ancestral sequences for an exiting alignment (this one available at <a href='http://wiki.prank-msa.googlecode.com/git/data/alignment_pep.fas'>alignment_pep.fas</a>).<br>
<br>
If the aim is infer ancestral codon sequences but the codon alignment itself is found too slow, one can make the alignment using the protein model and then infer the ancestors for the back-translated DNA alignment:<br>
<br>
<pre><code>prank -d=input.fas -o=output_translate -showall -translate<br>
prank -d=output_translate.best.nuc.fas -t=output_translate.best.dnd -o=output_translate_codon -keep -showall -codon<br>
</code></pre>
The ancestral sequences will be outputted to output_translate_codon.anc.fas.<br>
<br>
See <a href='http://code.google.com/p/prank-msa/wiki/PRANK?tm=6#Methods'>Methods</a> for more details.<br>
<br>
<br>

<h2>Finishing an alignment and merging two alignments</h2>

PRANK has new features that allow both aligning two alignments and finishing an alignment of a partially resolved dataset, consisting of one of more aligned sub-trees.<br>
<br>
In the first case, the two alignments and the corresponding trees (for example, <a href='http://wiki.prank-msa.googlecode.com/git/data/alignment_1.fas'>alignment_1.fas</a>, <a href='http://wiki.prank-msa.googlecode.com/git/data/alignment_2.fas'>alignment_2.fas</a>, <a href='http://wiki.prank-msa.googlecode.com/git/data/tree_1.tre'>tree_1.tre</a> and <a href='http://wiki.prank-msa.googlecode.com/git/data/tree_2.tre'>tree_2.tre</a>) are defined as<br>
<pre><code>prank -d1=alignment_1.fas -d2=alignment_2.fas -t1=tree_1.tre -t2=tree_2.tre -tree="(t1:0.1,t2:0.2);"<br>
</code></pre>

If no trees (<code>-t1=</code> and <code>-t2=</code>) are provided, PRANK will compute NJ trees for the two alignments and infer ancestors based on those. If no merge-tree (<code>-t=</code> or <code>-tree=</code>) is provided, the default branch length is used; that can be modified with option <code>-mergedist=</code>. The merging of the two alignments is based on the alignment of the two ancestors.<br>
<br>
In the second case, the sequences belonging to the same group are indicated by " group_XX" in the end of the name (where XX is unique for each group) and PRANK automatically finds the maximally large sub-trees consisting of sequences from the same group.<br>
<br>
This feature is best explained by an example. If you download files <a href='http://wiki.prank-msa.googlecode.com/git/data/example_partaligned.fas'>example_partaligned.fas</a> and <a href='http://wiki.prank-msa.googlecode.com/git/data/example.tre'>example.tre</a>, the alignment can be finished with the command:<br>
<pre><code>prank -d=example_partaligned.fas -t=example.tre -partaligned<br>
</code></pre>

When finishing an alignment, PRANK looks for maximally large sub-trees of  pre-aligned sequences belonging to the same group. If a sub-tree includes a sequence not from the same group, that sequence is normally aligned and also sequences outside that sequence (even if they belong to that group) will be re-aligned. This is again better explained by an example. If you download files <a href='http://wiki.prank-msa.googlecode.com/git/data/example_partaligned_2.fas'>example_partaligned_2.fas</a> and run the command:<br>
<pre><code>prank -d=example_partaligned_2.fas -t=example.tre -partaligned<br>
</code></pre>
you notice that many more nodes need to aligned in order to finish the complete alignment. Note that PRANK will fail if the group annotation does not match actual data and sequences assigned to a specific group are not truly aligned.<br>
<br>
<br>

<h2>Alignment reformatting and back-translation</h2>

PRANK supports several different alignment formats and can translate and back-translate sequence data between DNA and protein. These features can be exploited also without performing alignment of sequences.<br>
Example data used below can be found at <a href='http://wiki.prank-msa.googlecode.com/git/data/alignment_codon.fas'>alignment_codon.fas</a>, <a href='http://wiki.prank-msa.googlecode.com/git/data/alignment_pep.fas'>alignment_pep.fas</a> and <a href='http://wiki.prank-msa.googlecode.com/git/data/input_dna.fas'>input_dna.fas</a>.<br>
<br>
Option <code>-convert</code> tells to convert between formats. This is typically accompanied with option <code>-f=format</code> where <code>format</code> is either <code>fasta</code>, <code>phylipi</code>, <code>phylips</code>, <code>paml</code>, <code>nexus</code> or <code>raxml</code>. The input and output files are specified as normally with  options <code>-d=filename</code> and <code>-o=filename</code>; with options <code>-translate</code> and <code>-mttranslate</code> the DNA sequences are additionally translated to proteins. The command:<br>
<pre><code>prank -convert -d=alignment_codon.fas -translate -f=phylipi -o=alignment_pep -keep<br>
</code></pre>
converts a codon alignment in FASTA format to a protein alignment in interleaved PHYLIP format.<br>
<br>
If option <code>-dna=filename</code> is included, PRANK attempts to back-translate the input protein alignment to the corresponding DNA alignment. This assumes that the input alignment (<code>-d=filename</code>) is proteins and the the other file (<code>-dna=filename</code>) contains matching unaligned DNA sequences with identical names. The command:<br>
<pre><code>prank -convert -d=alignment_pep.fas -dna=input_dna.fas -o=alignment_dna -keep<br>
</code></pre>
converts a protein alignment in FASTA format to a DNA alignment in FASTA format.<br>
<br>
<br>
<br>
<BR><br>
<br>
<br>
<br>
<h1>Methods</h1>

<b>Models</b>

For DNA data, PRANK by default uses HKY model with empirical base frequencies and <code>kappa=2</code>. With the optional command parameters, it supports TN <a href='http://mbe.oxfordjournals.org/content/10/3/512.short'>(Tamura and Nei, 1993)</a> and models below it (JC, K2P, FEL, HKY). For example, JC model is defined as <code>-kappa=1 -dnafreqs=0.25,0.25,0.25,0.25</code>. WAG <a href='http://mbe.oxfordjournals.org/content/18/5/691.short'>(Whelan and Goldman, 2001)</a> is used for protein alignments.<br>
<br>
PRANK can do translated alignments of protein-coding DNA. It translates protein-coding DNA to protein sequences, aligns these sequences as proteins, and back-translates the resulting alignment to DNA such that the gaps are maintained. (PRANK can also back-translate protein alignments produced with external alignment software; see below for examples.)<br>
<br>
In addition to translated alignment, PRANK can also align codon sequences using a codon substitution matrix <a href='http://mbe.oxfordjournals.org/content/24/7/1464.short'>(Kosiol, Holmes and Goldman, 2007)</a>. Translation into amino acids and codons is done in the first forward frame without any error-checking. Based on independent benchmarks, codon alignment produces more accurate alignments than alignment of translated protein sequences.<br>
<br>
Simulation studies with nucleotide sequences containing high numbers of insertions and deletions showed that the option <code>-F</code> gives the most accurate results and should be used when the guide phylogeny can be trusted <a href='http://www.sciencemag.org/content/320/5883/1632.short'>(Löytynoja and Goldman, 2008)</a>.<br>
<br>
<b>Guide tree</b>

Progressive alignment requires a guide tree, and the algorithm of PRANK can be especially sensitive to errors in that. If a trusted pre-existing phylogeny with branch lengths is available for the input sequences (as often is in comparative genomic studies), it is recommended to use that.<br>
<br>
If no tree is provided, PRANK constructs one: it first call MAFFT <a href='http://nar.oxfordjournals.org/content/33/2/511.short'>(Katoh et al, 2005)</a> to make a quick alignment and infers an NJ tree from the evolutionary distances based on that; an alternative (and much slower) approach is to estimate the evolutionary distances from pairwise alignments generated by PRANK itself.<br>
<br>
By default, PRANK iterates the alignment five times and writes the solution with the best score to the file named <code>filename.best.fas</code>.  To prevent alignment iteration (e.g. when providing a guide tree that you trust), use the flag <code>-once</code> or <code>-iterate=1</code>.<br>
<br>
<b>Anchoring</b>

The standard PRANK algorithm is based on an exhaustive search of the best pairwise solution, and for long sequences this soon becomes too time consuming. By default PRANK uses Exonerate <a href='http://www.biomedcentral.com/1471-2105/6/31'>(Slater and Birney, 2005)</a> to anchor the pairwise alignments and thus speed up the process.<br>
<br>
<b>Ancestral reconstruction</b>

PRANK's own ancestral reconstruction happens during progressive alignment and is based on descendant sequences only. To improve the ancestral reconstruction, PRANK uses <code>BppAncestor</code> from the <code>BppSuite</code> package <a href='http://www.biomedcentral.com/1471-2148/8/255'>(Dutheil and  Boussau, 2008)</a> to infer the character states and then combines these with the inferred character presence/absence information. PRANK's optimization score is also based on these maximum likelihood inferences.<br>
<br>
<br>
<br>
<br>
<br>
<BR><br>
<br>
