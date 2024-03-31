# Turn list of Chinese sentences or words into Anki cards using Google Sheets

Install the mandarin-cantonese-api:
http://api-docs.mandarincantonese.com/
This lets you use =PINYIN(...) as a formula

Then use the following formulas:

Column A:
original simplified list of terms / phrases

B:
=googletranslate(A1,"zh_CN","zh_TW")

C:
=pinyin(A1)

D:
=googletranslate(A1)

E:
=CONCATENATE(importxml(concatenate("https://www.mdbg.net/chinese/dictionary?page=worddict&wdrst=0&wdqb=",A1),"//div[@class='defs']"))



Fill those down to cover your whole list.

B will convert simplified to traditional. Reverse the arguments if your source text is traditional (and remember to align the fields correctly on import).

D will autodetect the language and provide an English translation that is of questionable accuracy. Best for longer sentences. I tend not to use this.

E pulls definitions from MDBG, which is much more accurate in many cases, especially words and chengyu. But it can be slow. 

