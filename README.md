# WOMBAT
Word Embedding Database

See <a href="http://arxiv.org/abs/1807.00717" target="_blank">this paper</a> (to appear at <a href="http://coling2018.org/accepted-demo-papers/" target="_blank">COLING 2018</a>) for more details.


<pre>
 |                                   | 
 |             ,.--""""--.._         |
 |           ."     .'      `-.      |
 |          ;      ;           ;     |
 |         '      ;             )    |
 |        /     '             . ;    |
 |       /     ;     `.        `;    |
 |     ,.'     :         .    : )    |
 |     ;|\'    :     `./|) \  ;/     |
 |     ;| \"  -,-  "-./ |;  ).;      |
 |     /\/             \/   );       |
 |    :                \     ;       |
 |    :     _      _     ;   )       |
 |    `.   \;\    /;/    ;  /        |
 |      !    :   :     ,/  ;         |
 |       (`. : _ : ,/     ;          |
 |        \\\`"^" ` :    ;           |   This is WOMBAT, the WOrd eMBedding dATa base API (Version 2.0)
 |                (    )             |
 |                 ////              |
 |                                   |
 | Wombat artwork by akg             |
 |            http://wombat.ascii.uk |
</pre>

<b>WOMBAT</b>, the WOrd eMBedding dATabase, is a light-weight Python tool for more transparent, efficient, and robust access to potentially large numbers of word embedding collections (WECs). 
It supports NLP researchers and practitioners in developing compact, efficient, and reusable code. 
Key features of WOMBAT are
<ol type=1>
<li>transparent identification of WECs by means of a clean syntax and human-readable features, </li>
<li>efficient lazy, on-demand retrieval of word vectors, and</li> 
<li>increased robustness by systematic integration of executable preprocessing code. </li>
</ol>

WOMBAT implements some Best Practices for research reproducibility and complements existing approaches towards WEC standardization and sharing. 
WOMBAT provides a single point of access to existing WECs. Each plain text WEC file has to be imorted into WOMBAT once, receiving in the process a set of ATT:VAL identifiers consisting of five system attributes (algo, dims, dataset, unit, fold) plus arbitrarily many user-defined ones.

<h3>Importing Pre-Trained Embeddings to WOMBAT: GloVe</h3>
One of the main uses of WOMBAT is as a wrapper for accessing existing, off-the-shelf word embeddings like e.g. GloVe. (The other use involves access to self-trained embeddings, including tokenization and handling of multi-word-expressions, cf. below.)

The following code is sufficient to import a sub set of the GloVe embeddings. 
<pre>
from wombat_api.core import connector as wb_conn
wbpath="data/wombat-data/"
importpath="data/embeddings/"
wbc = wb_conn(path=wbpath, create_if_missing=True)
for d in ['50', '100', '200', '300']:
    wbc.import_from_file(importpath+"glove.6B."+d+"d.txt", 
                         "algo:glove;dataset:6b;dims:"+d+";fold:1;unit:token")
</pre>

The required GloVe embeddings can be obtained from Stanford <a href="http://nlp.stanford.edu/data/wordvecs/glove.6B.zip">here</a>, and need to be extracted into "data/embeddings/".

The WOMBAT master and embeddings data bases will be created in "data/wombat-data". 

The above import assigns only the minimally required ATT:VAL pairs to the embeddings:
<table>
<tr>
<td>hh</td>
</tr>
</table>
