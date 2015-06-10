## Previously Asked Questions ##

**Q:** PRANK is slow. Is there a multi-threaded/parallelised version of the program?

**A:** No but the alignment anchoring introduced in a recent version of the program can speed up the analyses by several orders of magnitude.

<br>

<b>Q:</b> PRANK alignment requires (and depends on) a guide tree. I don't know the positions of all taxa/sequences, what should I do?<br>
<br>
<b>A:</b> You could test my other program PAGAN that can be found <a href='http://code.google.com/p/pagan-msa/'>here</a>. You could align the known sequences with PRANK or PAGAN, and then extend this alignment with the rest of the sequences using PAGAN.<br>
<br>
<br>

<b>Q:</b> Some of my sequences are very short. Can PRANK handle them?<br>
<br>
<b>A:</b> It should be pretty good with sequences of different length but my other program PAGAN may do even better. See the previous question and replace "unknown sequences" with "short sequences".