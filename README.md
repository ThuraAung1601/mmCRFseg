# mmCRFseg : Myanmar Word Segmentation using Conditional Random Fields

Word Segmentation for Myanmar Language using Conditional Random Fields with character tagging - 1 for beginning of sentences and 0 for others.

```{r, engine='bash', count_lines}
ဪ ၊ အခန်း နံပါတ် ၃၀၅ မှာ တည်း လို့ ရ ပါ တယ် ။ အေးအေးဆေးဆေး ရှိ ပါ တယ် ။
```

```{r, engine='bash', count_lines}
[('ဪ', 0), ('၊', 1), ('အ', 1), ('ခ', 0), ('န', 0), ('်', 0), ('း', 0), ('န', 1), ('ံ', 0), ('ပ', 0), ('ါ', 0), ('တ', 0), ('်', 0), ('၃', 1), ('၀', 0), ('၅', 0), ('မ', 1), ('ှ', 0), ('ာ', 0), ('တ', 1), ('ည', 0), ('်', 0), ('း', 0), ('လ', 1), ('ိ', 0), ('ု', 0), ('့', 0), ('ရ', 1), ('ပ', 1), ('ါ', 0), ('တ', 1), ('ယ', 0), ('်', 0), ('။', 1), ('အ', 1), ('ေ', 0), ('း', 0), ('အ', 0), ('ေ', 0), ('း', 0), ('ဆ', 0), ('ေ', 0), ('း', 0), ('ဆ', 0), ('ေ', 0), ('း', 0), ('ရ', 1), ('ှ', 0), ('ိ', 0), ('ပ', 1), ('ါ', 0), ('တ', 1), ('ယ', 0), ('်', 0), ('။', 1)]
```

|                             | Scores       |
|:---------------------------:|:------------:|
| Precision                   | 0.959        |
| Recall                      | 0.953        |
| Accuracy                    | 0.980        |

It was trained and tested on myPOS corpus version 3.0[1] based on the study of Win Pa Pa et al.[2]. Although this tool is built just for educational purpose only, the speed and accuracy proved its reliability for real-world applications.

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
from seg import segment_word
sentence = "ဒီနေ့ကမ္ဘာ့စံချိန်သစ်တင်ခဲ့တယ်။"
segment_word(sentence)
```

Output: "ဒီ နေ့ ကမ္ဘာ့ စံချိန် သစ်တင် ခဲ့ တယ် ။"


```{r, engine='bash', count_lines}
from seg import segment_word
sentence = "မိုးရွာထားလို့အခန်းထဲမှာစိုထိုင်းထိုင်းဖြစ်နေတယ်"
segment_word(sentence)
```

Output: "မိုးရွာ ထား လို့ အခန်း ထဲ မှာ စိုထိုင်း ထိုင်း ဖြစ် နေ တယ်"

```{r, engine='bash', count_lines}
from seg import segment_word
sentences = "မောက်ချိုက်အရသာလေးက ပေါ့တဲ့ဘက်သွားတော့ အငန်မစားတဲ့သူဆို အတော်ပဲ ဆိုင်ကတမင် အငန်မစားတဲ့သူတွေအဆင်ပြေအောင်လျော့ထားပုံရတယ်"
segment_word(sentences)
```
Output: 'မောက်ချိုက် အရသာလေး က ပေါ့ တဲ့ ဘက် သွား တော့ အငန် မ စား တဲ့ သူ ဆို အတော် ပဲ ဆိုင် ကတမင် အငန် မ စား တဲ့ သူ တွေ အဆင်ပြေ အောင် လျော့ ထား ပုံ ရ တယ်'

```{r, engine='bash', count_lines}
from seg import segment_word
sentences = "ကိုရိုနာဗိုင်းရပ်စ် ဆိုတာ လူနဲ့ တခြားတိရစ္ဆာန်တွေကို ကူးစက်တတ်တဲ့ ဗိုင်းရပ်စ် တစ်မျိုး ဖြစ်ပါတယ် အကြမ်းအားဖြင့် လူသားတွေအကြားမှာ ကူးစက်ပြန့်ပွားပြီး ချောင်းဆိုးတာ ကိုယ်ပူတာနဲ့ နှာရည်ယိုတာတွေလို သာမန် အဖျားရောဂါနဲ့ ဆင်တူတဲ့ လက္ခဏာတွေကို ဖြစ်စေပါတယ်"
segment_word(sentences)
```
Output: ကိုရိုနာ ဗိုင်းရပ်စ် ဆို တာ လူ နဲ့ တခြား တိရစ္ဆာန် တွေ ကို ကူးစက် တတ် တဲ့ ဗိုင်းရပ်စ် တစ် မျိုး ဖြစ် ပါတယ် အကြမ်း အားဖြင့် လူသား တွေ အကြား မှာ ကူးစက် ပြန့်ပွား ပြီး ချောင်းဆိုးတာ ကိုယ်ပူတာ နဲ့ နှာရည် ယို တာ တွေ လို သာမန် အဖျား ရောဂါ နဲ့ ဆင်တူ တဲ့ လက္ခဏာ တွေ ကို ဖြစ် စေ ပါတယ် 

## References

[1] Zar Zar Hlaing, Ye Kyaw Thu, Myat Myo Nwe Wai, Thepchai Supnithi, Ponrudee Netisopakul, "Myanmar POS resource extension effects on automatic tagging methods", In Proceedings of the 15th International Joint Symposium on Artificial Intelligence and Natural Language Processing (iSAI-NLP 2020), Nov 18 to Nov 20, 2020, Bangkok, Thailand, pp. 189-194. [Paper]

[2] Win Pa Pa, Ye Kyaw Thu, Andrew M. Finch and Eiichiro Sumita. “Word Boundary Identification for Myanmar Text Using Conditional Random Fields.” ICGEC (2015).

[3] myWord: Syllable, Word and Phrase Segmenter for Burmese, Ye Kyaw Thu, Sept 2021, GitHub Link: https://github.com/ye-kyaw-thu/myWord  

[4] Myan-word-breaker : Nay Lin Aung, https://github.com/stevenay/myan-word-breaker 

[5] pyidaungsu : Kaung Htet San : https://github.com/kaunghtetsan275/pyidaungsu
