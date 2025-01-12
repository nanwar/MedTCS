# MedTCS

This is the official code repository for the Frontiers in Molecular Biosciences, 12 August 2022 Sec. Molecular Diagnostics and Therapeutic paper [Medical terminology-based computing system: a lightweight post-processing solution for out-of-vocabulary multi-word terms](https://www.frontiersin.org/articles/10.3389/fmolb.2022.928530/full#.YyPtkbGGAT1.linkedin) by [Nadia Saeed](https://twitter.com/i181606), and [Hammad Naveed](https://www.linkedin.com/in/hammad-naveed-a310782/).
The research composed a **Med**ical **T**erminology based **C**omputing **S**ystem (MedTCS): a
lightweight post-processing solution for out-of-vocabulary(OOV) multi-word terms. 
MedTCS is a natural language processing system helps the distributed representation models (like: Word2Vec, GloVe) to handle the OOV problem effectively. 

The below image shows how the biomedical/clinical terms components deliver a maningful information.

![](Figure1.png)

## Meta-data Collection
In MedTCS, we have build meta-dictionaries for the prefixes, roots, and suffixes defining the meanings of medical term components. The three semantic
dictionaries contain 467 [root words](https://github.com/NadiaSaeed/MedTCS/blob/9406ab861c60de0d1026d88261409051b3ee4106/MedTCS-root.csv), 432 [prefixes](https://github.com/NadiaSaeed/MedTCS/blob/9406ab861c60de0d1026d88261409051b3ee4106/MedTCS-prefix.csv), and 112 [suffixes](https://github.com/NadiaSaeed/MedTCS/blob/9406ab861c60de0d1026d88261409051b3ee4106/MedTCS-suffix.csv), along with their corresponding
meanings as shown in [Fig 1](https://github.com/NadiaSaeed/MedTCS/blob/9406ab861c60de0d1026d88261409051b3ee4106/Figure1.png).


## MedTCS Framework
MedTCS module to encode OOV words from a set of sentences or words have following steps:   
- OOV Word Detector   
- Pluralizer/Singularizer     
- Term Parser    
- Term Segmenter      
     

## MedTCS:Term Segmenter model
The pre-trained [term segmenter model](https://github.com/NadiaSaeed/MedTCS/blob/9406ab861c60de0d1026d88261409051b3ee4106/Morphmodel.bin) returned meaningful sub-words of an unknown term (like seasickness → sea+sick+ness).

## Example
| Mode       |Sentences        |
| ------------- |:-------------:|
|Original Input    | flavoxate hydrochloride tablets are indicated for symptomatic relief of dysuria urgency **<ins>nocturia</ins>** **<ins>suprapubic</ins>** pain frequency and incontinence as may occur in cystitis prostatitis urethritis **<ins>urethrocystitis</ins>** **<ins>urethrotrigonitis</ins>** |
|OOV Term    | flavoxate hydrochloride tablets are indicated for symptomatic relief of dysuria urgency **<ins>OOV</ins>** **<ins>OOV</ins>** pain frequency and incontinence as may occur in cystitis prostatitis urethritis **<ins>OOV</ins>** **<ins>OOV</ins>** |
|MedTCS’s Input to Encoder    | flavoxate hydrochloride tablets are indicated for symptomatic relief of dysuria urgency **<ins>night urination urine above excessive</ins>** **<ins>superior pubis portion of pelvic bone ic</ins>** pain frequency and incontinence as may occur in cystitis prostatitis urethritis **<ins>urethra bladder or cyst inflammation</ins>** **<ins>urethra trigone inflammation</ins>** |

Above sentence took from [RxList](https://www.rxlist.com/flavoxate-side-effects-drug-center.htm) and OOV terms observed in [GloVe-Twitter-200d](https://nlp.stanford.edu/projects/glove/) that estimate with MedTCS.



[MedTCS module](https://github.com/NadiaSaeed/MedTCS/blob/9406ab861c60de0d1026d88261409051b3ee4106/MedTCS.ipynb) enabled the word embedding models to encode the vector for OOV terms from its search-space effectively.
