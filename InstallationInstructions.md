<br>

<br>
<br>
<br>


<h1>Automatic check for new versions of PRANK</h1>

PRANK includes an option to easily check if program updates are available. With command<br>
<pre><code>prank -version<br>
</code></pre>
the PRANK checks for updates and lists the changes in the new version.<br>
<br>
<br>


<h1>Pre-compiled executables for Windows</h1>

The pre-compiled executables are available via the <a href='http://code.google.com/p/prank-msa/downloads/list'>Downloads tab</a>.<br>
<br>
It is recommended to place the unpacked content of the zip file to the directory "Program Files". Here we assume that the file path to the directory "prank" is <code>C:\Program Files\prank</code>.<br>
<br>
For the ease of use, it is recommended to add the directory <code>prank/bin</code> permanently to the system path. On Windows 7, this can be done through the following steps:<br>
<br>
<ul><li>open "Control Panel"<br>
</li><li>choose "System"<br>
</li><li>on the left panel, choose "Advanced system settings"<br>
</li><li>on the new window, click "Environment Variables"<br>
</li><li>find "Path" in the lower field, select it and click "Edit"<br>
</li><li>leave the existing content intact and add  <b><code>;C:\"Program Files"\prank</code></b>  in the end of the field "Variable value"<br>
</li><li>click "OK" three times and close "Control Panel"</li></ul>

If you now open Command Prompt and write <code>prank</code>, the program should run and show the options list.<br>
<br>
The executable has been compiled and tested on Windows 7 (32bit) system.<br>
<br>
<h2>Hints for using PRANK on Windows</h2>

PRANK is used through commands given in Command Prompt. For those not familiar with moving around files, the following workflow may be useful.<br>
<br>
<ul><li>open "Command Prompt" from "All Programs" -> "Accessories"<br>
</li><li>in Command Prompt, type commands<br>
<pre><code>mkdir analysis<br>
cd analysis<br>
explorer .<br>
</code></pre>
</li><li>drag and drop your alignment input file(s) to the Explorer window that was opened<br>
</li><li>in Command Prompt, run PRANK as <code>prank -d=myfile [other options]</code>
</li><li>once finished, the result files will appear in the Explorer window</li></ul>

<br>

<h1>Pre-compiled executables for Mac OSX</h1>

The pre-compiled executables are available via the <a href='http://code.google.com/p/prank-msa/downloads/list'>Downloads tab</a>.<br>
<br>
The PRANK executable for Mac has been compiled on OSX 10.8. The package contains the PRANK executable and its manual page (read it with command <code>man ./prank/prank.1</code>) as well as MAFFT and Exonerate executables and the necessary files for those to work correctly.<br>
<br>
The PRANK package file can be downloaded and unpacked using graphical software. With the command line, the same can be done with the commands:<br>
<pre><code>mkdir ~/programs<br>
cd ~/programs<br>
curl -O http://prank-msa.googlecode.com/files/prank.osx64.130820.tgz<br>
tar xvzf prank.osx64.130820.tgz<br>
./prank/bin/prank<br>
</code></pre>
For the ease of use, it is recommended to add the directory <code>prank/bin</code> to the system path or copy its content to a such directory (such as <code>~/bin</code> or <code>/usr/local/bin</code>). This can be done with commands similar to these:<br>
<pre><code>echo "export PATH=$PATH:/Users/$USER/programs/prank/bin" &gt;&gt; ~/.bash_profile<br>
</code></pre>
or<br>
<pre><code>cp -R /Users/$USER/programs/prank/bin/* ~/bin/<br>
</code></pre>
Note that if the executables are moved or copied, the directory structure (<code>bin/mafftlib</code>) and the location of library dependencies have to be retained.<br>
<br>
<br>

<h1>Pre-compiled executables for Linux</h1>

The pre-compiled executables are available via the <a href='http://code.google.com/p/prank-msa/downloads/list'>Downloads tab</a>.<br>
<br>
The PRANK executable for Linux has been compiled on Red Hat 5.8 (64bit) and confirmed to work also on Ubuntu 12.04 and CentOS 6.0.<br>
<br>
Using the command line, the PRANK executable for Linux can be downloaded and unpacked with the commands:<br>
<pre><code>mkdir ~/programs<br>
cd ~/programs<br>
wget http://prank-msa.googlecode.com/files/prank.linux64.130820.tgz<br>
tar prank.linux64.130820.tgz<br>
./prank/bin/prank<br>
</code></pre>

For the ease of use, it is recommended to add the directory <code>prank/bin</code> to the system path or copy its content to a such directory (such as <code>~/bin</code> or <code>/usr/local/bin</code>). This can be done with commands similar to these:<br>
<pre><code>echo "export PATH=$PATH:/home/$USER/programs/prank/bin" &gt;&gt; ~/.bash_profile<br>
</code></pre>
or<br>
<pre><code>cp -R /home/$USER/programs/prank/bin/* ~/bin/<br>
</code></pre>
Note that if the executables of the bundled version are moved or copied, the directory structure (<code>bin/lib</code>) and the location of library dependencies have to be retained.<br>
<br>
<br>
<br>

<h1>Installation of PRANK from source code</h1>

You can download a snapshot of the PRANK code from the <a href='http://code.google.com/p/prank-msa/downloads/list'>Downloads page</a> and get the latest version using <code>git</code> as explained on the <a href='http://code.google.com/p/prank-msa/source/checkout'>Source page</a>. On command line, the process looks like this (tested on Linux and MacOSX):<br>
<br>
<pre><code>wget http://prank-msa.googlecode.com/files/prank.source.130820.tgz<br>
# OR<br>
curl -O http://prank-msa.googlecode.com/files/prank.source.130820.tgz<br>
<br>
tar xvzf prank.source.130820.tgz<br>
cd prank-msa/src<br>
make<br>
./prank<br>
<br>
[ cp prank ~/bin ]<br>
[ sudo cp prank /usr/bin ]<br>
</code></pre>

or<br>
<br>
<pre><code>git clone http://code.google.com/p/prank-msa/ <br>
cd prank-msa/src<br>
make<br>
./prank<br>
<br>
[ cp prank ~/bin ]<br>
[ sudo cp prank /usr/bin ]<br>
<br>
</code></pre>

On Windows, the PRANK source code has been verified to compile on the <a href='http://cygwin.com/'>Cygwin environment</a>.<br>
<br>
<br>

<h2>Optional: Installation of MAFFT, Exonerate and <code>BppAncestor</code></h2>

For the fast guide tree estimation, alignment anchoring and ancestral reconstruction to work, you need to have MAFFT, Exonerate and <code>BppAncestor</code> installed and on the execution path.<br>
You can download the MAFFT source code from <a href='http://www.ebi.ac.uk/~guy/exonerate/'>http://www.ebi.ac.uk/~guy/exonerate/</a> and the Exonerate source code from <a href='http://mafft.cbrc.jp/alignment/software/'>http://mafft.cbrc.jp/alignment/software/</a> and follow the instructions for their installation.<br>
On many popular Linux distributions MAFFT and Exonerate are available in the software repository and can be installed pre-compiled.<br>
On Ubuntu, that is done with the following commands:<br>
<pre><code>sudo apt-get install mafft<br>
sudo apt-get install exonerate<br>
</code></pre>

Because of dependencies in Exonerate, also on MacOSX the installation is easier with a package management system such as <a href='http://mxcl.github.com/homebrew/'>Homebrew</a>. On OSX 10.7, Exonerate can be installed with the following commands:<br>
<pre><code>sudo /usr/bin/ruby -e "$(curl -fsSL https://raw.github.com/gist/323731)"<br>
sudo brew install pkg-config<br>
sudo brew install exonerate<br>
</code></pre>
See <a href='http://mxcl.github.com/homebrew/'>http://mxcl.github.com/homebrew/</a> for further details.<br>
<br>
<code>BppSuite</code> is provided as pre-compiled binaries for several platforms at <a href='http://home.gna.org/bppsuite/'>http://home.gna.org/bppsuite/</a> and is also available in repositories of some popular Linux distros. Unfortunately, the version of <code>BppAncestor</code> provided there probably contains a critical bug and cannot be used. The commands below compile the program suite against the latest version of the Bpp libraries.<br>
<br>
<pre><code>mkdir bppsuite<br>
cd bppsuite/<br>
bpp_dir=`pwd`<br>
<br>
mkdir sources <br>
cd sources/<br>
<br>
git clone http://biopp.univ-montp2.fr/git/bpp-core<br>
git clone http://biopp.univ-montp2.fr/git/bpp-seq<br>
git clone http://biopp.univ-montp2.fr/git/bpp-phyl<br>
<br>
svn co svn://svn.gna.org/svn/bppsuite/trunk bppsuite<br>
<br>
cd bpp-core/<br>
cmake -D CMAKE_INSTALL_PREFIX=$bpp_dir -D CMAKE_LIBRARY_PATH=$bpp_dir/lib -D CMAKE_INCLUDE_PATH=$bpp_dir/include -D  BUILD_TESTING=FALSE -D CMAKE_EXE_LINKER_FLAGS=-static ./<br>
make<br>
make install<br>
<br>
cd ../bpp-seq/<br>
cmake -D CMAKE_INSTALL_PREFIX=$bpp_dir -D CMAKE_LIBRARY_PATH=$bpp_dir/lib -D CMAKE_INCLUDE_PATH=$bpp_dir/include -D  BUILD_TESTING=FALSE -D CMAKE_EXE_LINKER_FLAGS=-static ./<br>
make<br>
make install<br>
<br>
cd ../bpp-phyl/<br>
cmake -D CMAKE_INSTALL_PREFIX=$bpp_dir -D CMAKE_LIBRARY_PATH=$bpp_dir/lib -D CMAKE_INCLUDE_PATH=$bpp_dir/include -D  BUILD_TESTING=FALSE -D CMAKE_EXE_LINKER_FLAGS=-static ./<br>
make<br>
make install<br>
<br>
cd ../bppsuite/<br>
cmake . -DCMAKE_PREFIX_PATH=$bpp_dir -DCMAKE_INSTALL_PREFIX=$bpp_dir -DCMAKE_EXE_LINKER_FLAGS=-static -DBUILD_STATIC=true<br>
make<br>
make install<br>
<br>
cd ../../bin/<br>
ls |xargs strip<br>
<br>
</code></pre>

<br>