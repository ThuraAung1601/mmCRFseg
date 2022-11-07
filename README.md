# Myanmar Word Segmentation using Conditional Random Field

Word Segmentation for Myanmar Language using Conditional Random Fields ( with character features )

- Precision: 0.9593931034482759
- Recall: 0.9539719113451832
- Accuracy: 0.9800131976345778

It was trained and tested on myPOS corpus version 3.0[1] based on the study of Win Pa Pa et al.[2]. This tool is built just for educational purpose only.

## Other useful text segmentation tools for Myanmar Langauge
- myWord[3] : syllable, word, sub_word and phrase segmenter for Burmese <br />
( Highly recommend : **most accurate because of its large dictionary sizes, different approaches for different tokens units** )

- Myan-word-breaker[4] : Statistical approach based word segmentation

- pyidaungsu[5] : Python text processing library for Myanmar language <br />
( Many future works and still under development. It also used CRF model for word segmentation. )

## Download repo

```{r, engine='bash', count_lines}
git clone https://github.com/ThuraAung1601/mm-Word-Seg
```

## Install requirement

```{r, engine='bash', count_lines}
pip install -r python-crfsuite
```

## How to run

တစ်ဖိုင်လုံး Segmentation လုပ်ချင်တဲ့ ဖိုင် ရှိရင် ဒီလို အသုံးပြုပါ။

```{r, engine='bash', count_lines}
python ./seg.py -i test.txt -o out.txt
```

```{r, engine='bash', count_lines}
$ python seg.py --help
usage: seg.py [-h] [-i INPUT] [-o OUTPUT]

Word Segmentation for Burmese language using CRF model

optional arguments:
  -h, --help            show this help message and exit
  -i INPUT, --input INPUT
                        input file
  -o OUTPUT, --output OUTPUT
                        output file
```

တခြား Program ​တွေထဲ ထည့်သုံးချင်ရင် ဒီလို ​ခေါ် သုံးလို့ ရပါတယ်။

```{r, engine='bash', count_lines}
from seg import segment_sentence
sentence = "ဒီနေ့ကမ္ဘာ့စံချိန်သစ်တင်ခဲ့တယ်။"
segment_word(sentence)
```

Output : "ဒီ နေ့ ကမ္ဘာ့ စံချိန် သစ်တင် ခဲ့ တယ် ။"


```{r, engine='bash', count_lines}
from seg import segment_sentence
sentence = "မိုးရွာထားလို့အခန်းထဲမှာစိုထိုင်းထိုင်းဖြစ်နေတယ်"
segment_word(sentence)
```

Output : "မိုးရွာ ထား လို့ အခန်း ထဲ မှာ စိုထိုင်း ထိုင်း ဖြစ် နေ တယ်"

```{r, engine='bash', count_lines}
from seg import segment_word
sentences = "မောက်ချိုက်အရသာလေးက ပေါ့တဲ့ဘက်သွားတော့ အငန်မစားတဲ့သူဆို အတော်ပဲ ဆိုင်ကတမင် အငန်မစားတဲ့သူတွေအဆင်ပြေအောင်လျော့ထားပုံရတယ်"
segment_word(sentences)
```
Output : 'မောက်ချိုက် အရသာလေး က ပေါ့ တဲ့ ဘက် သွား တော့ အငန် မ စား တဲ့ သူ ဆို အတော် ပဲ ဆိုင် ကတမင် အငန် မ စား တဲ့ သူ တွေ အဆင်ပြေ အောင် လျော့ ထား ပုံ ရ တယ်'


## References

[1] Zar Zar Hlaing, Ye Kyaw Thu, Myat Myo Nwe Wai, Thepchai Supnithi, Ponrudee Netisopakul, "Myanmar POS resource extension effects on automatic tagging methods", In Proceedings of the 15th International Joint Symposium on Artificial Intelligence and Natural Language Processing (iSAI-NLP 2020), Nov 18 to Nov 20, 2020, Bangkok, Thailand, pp. 189-194. [Paper]

[3] myWord: Syllable, Word and Phrase Segmenter for Burmese, Ye Kyaw Thu, Sept 2021, GitHub Link: https://github.com/ye-kyaw-thu/myWord  

[4] Myan-word-breaker : Nay Lin Aung, https://github.com/stevenay/myan-word-breaker 

[5] pyidaungsu : Kaung Htet San : https://github.com/kaunghtetsan275/pyidaungsu
