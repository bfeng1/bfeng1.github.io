## Dive into Large Language Models: BBPE tokenizer
**Project description:** 
Unless you have been living under a rock, I am sure that you have heard, used, or even worked on some generative AIs. I have been amazed by the ChatGPT when it was first released in 2022. I have been wondering how this thing works, it feels like some dark magic. Over the years, this new AI hype has never trended down, but it has been recognized as the next economic engine for decades to come.

If you are someone like me, you might find it exciting to pursue a deeper technical understanding of generative AI. This is a huge topic and there are so many different concepts that are worth to be studied and researched. So we will only focus on one concept in this post: the tokenization behind most state-of-the-art large language models (LLMs).

For many LLMs, the quality of the tokenization determines the quality of the training data fed into the neuron network. In many cases, the root causes of many LLMs' issues are related to the tokenization used. So it is important to build a solid knowledge foundation on this topic if we want to pursue a deeper understanding of the LLMs and other generative AIs.

**Main Objectives**

BBPE (Byte Level Byte Pair Encoding) tokenizer was brought to the public's attention by OpenAI in their GPT2 paper. It gains more popularity afterwards and it now becomes the standard practice at the start of art LLMs. So this post, we will go through the following sections that aim to understand how BBPE works, and why they are popular compared to other types of tokenizers.

### 1. Why BBPE? 


Based on the analysis of various tokenization approaches, it becomes evident that each method presents unique advantages and challenges. The endeavor to devise a word-level tokenizer encompassing all languages necessitates an extensive vocabulary, including variations of words and characters. TransformerXL, a word-level tokenizer, exemplifies this with a vocabulary size of 267,735, illustrating the monumental task of comprehensive coverage.

Alternatively, employing a character-level Unicode tokenizer demonstrates efficacy across diverse languages, leveraging Unicode's exhaustive character set. However, this method entails considerable overhead due to the vast number of characters and the evolving nature of the Unicode standard, potentially leading to compatibility issues with older tokenizers.

UTF-8 encoding offers a compromise by yielding byte tokens with a modest base vocabulary, albeit resulting in lengthy token sequences. Yet, this presents a challenge for transformer-based language models due to attention length limitations, necessitating text compression to enhance efficiency while maintaining vocabulary size balance.

The BBPE (Byte Pair Encoding) tokenizer, as proposed in the GPT2 paper, addresses these concerns adeptly. By combining byte-level encoding with BPE algorithms, it achieves a small base vocabulary of 256 while allowing dynamic expansion through merge rules, facilitating effective token compression and adaptable vocabulary sizing. Consequently, BBPE emerges as a pragmatic solution, offering the flexibility to tailor vocabulary size to specific requirements without compromising efficiency or coverage.

### 2. Implement BBPE by steps

In this section, we have gone through each block to build a BBPE tokenizer from scratch. After training the tokenizer, we built the encoding and decoding functionalities as well and used a random text to test the results. 

1. Convert texts to raw bytes
2. find the most frequent pair in the whole sequence
3. replace the most frequent pair with a new ID
4. Train a BBPE tokenizer with all the steps above
5. Encoding and Decoding

**Vocabulary (with predetermined size of 280)**
```
{0: b'\x00', 1: b'\x01', 2: b'\x02', 3: b'\x03', 4: b'\x04', 5: b'\x05', 6: b'\x06', 7: b'\x07', 8: b'\x08', 9: b'\t', 10: b'\n', 11: b'\x0b', 12: b'\x0c', 13: b'\r', 14: b'\x0e', 15: b'\x0f', 16: b'\x10', 17: b'\x11', 18: b'\x12', 19: b'\x13', 20: b'\x14', 21: b'\x15', 22: b'\x16', 23: b'\x17', 24: b'\x18', 25: b'\x19', 26: b'\x1a', 27: b'\x1b', 28: b'\x1c', 29: b'\x1d', 30: b'\x1e', 31: b'\x1f', 32: b' ', 33: b'!', 34: b'"', 35: b'#', 36: b'$', 37: b'%', 38: b'&', 39: b"'", 40: b'(', 41: b')', 42: b'*', 43: b'+', 44: b',', 45: b'-', 46: b'.', 47: b'/', 48: b'0', 49: b'1', 50: b'2', 51: b'3', 52: b'4', 53: b'5', 54: b'6', 55: b'7', 56: b'8', 57: b'9', 58: b':', 59: b';', 60: b'<', 61: b'=', 62: b'>', 63: b'?', 64: b'@', 65: b'A', 66: b'B', 67: b'C', 68: b'D', 69: b'E', 70: b'F', 71: b'G', 72: b'H', 73: b'I', 74: b'J', 75: b'K', 76: b'L', 77: b'M', 78: b'N', 79: b'O', 80: b'P', 81: b'Q', 82: b'R', 83: b'S', 84: b'T', 85: b'U', 86: b'V', 87: b'W', 88: b'X', 89: b'Y', 90: b'Z', 91: b'[', 92: b'\\', 93: b']', 94: b'^', 95: b'_', 96: b'`', 97: b'a', 98: b'b', 99: b'c', 100: b'd', 101: b'e', 102: b'f', 103: b'g', 104: b'h', 105: b'i', 106: b'j', 107: b'k', 108: b'l', 109: b'm', 110: b'n', 111: b'o', 112: b'p', 113: b'q', 114: b'r', 115: b's', 116: b't', 117: b'u', 118: b'v', 119: b'w', 120: b'x', 121: b'y', 122: b'z', 123: b'{', 124: b'|', 125: b'}', 126: b'~', 127: b'\x7f', 128: b'\x80', 129: b'\x81', 130: b'\x82', 131: b'\x83', 132: b'\x84', 133: b'\x85', 134: b'\x86', 135: b'\x87', 136: b'\x88', 137: b'\x89', 138: b'\x8a', 139: b'\x8b', 140: b'\x8c', 141: b'\x8d', 142: b'\x8e', 143: b'\x8f', 144: b'\x90', 145: b'\x91', 146: b'\x92', 147: b'\x93', 148: b'\x94', 149: b'\x95', 150: b'\x96', 151: b'\x97', 152: b'\x98', 153: b'\x99', 154: b'\x9a', 155: b'\x9b', 156: b'\x9c', 157: b'\x9d', 158: b'\x9e', 159: b'\x9f', 160: b'\xa0', 161: b'\xa1', 162: b'\xa2', 163: b'\xa3', 164: b'\xa4', 165: b'\xa5', 166: b'\xa6', 167: b'\xa7', 168: b'\xa8', 169: b'\xa9', 170: b'\xaa', 171: b'\xab', 172: b'\xac', 173: b'\xad', 174: b'\xae', 175: b'\xaf', 176: b'\xb0', 177: b'\xb1', 178: b'\xb2', 179: b'\xb3', 180: b'\xb4', 181: b'\xb5', 182: b'\xb6', 183: b'\xb7', 184: b'\xb8', 185: b'\xb9', 186: b'\xba', 187: b'\xbb', 188: b'\xbc', 189: b'\xbd', 190: b'\xbe', 191: b'\xbf', 192: b'\xc0', 193: b'\xc1', 194: b'\xc2', 195: b'\xc3', 196: b'\xc4', 197: b'\xc5', 198: b'\xc6', 199: b'\xc7', 200: b'\xc8', 201: b'\xc9', 202: b'\xca', 203: b'\xcb', 204: b'\xcc', 205: b'\xcd', 206: b'\xce', 207: b'\xcf', 208: b'\xd0', 209: b'\xd1', 210: b'\xd2', 211: b'\xd3', 212: b'\xd4', 213: b'\xd5', 214: b'\xd6', 215: b'\xd7', 216: b'\xd8', 217: b'\xd9', 218: b'\xda', 219: b'\xdb', 220: b'\xdc', 221: b'\xdd', 222: b'\xde', 223: b'\xdf', 224: b'\xe0', 225: b'\xe1', 226: b'\xe2', 227: b'\xe3', 228: b'\xe4', 229: b'\xe5', 230: b'\xe6', 231: b'\xe7', 232: b'\xe8', 233: b'\xe9', 234: b'\xea', 235: b'\xeb', 236: b'\xec', 237: b'\xed', 238: b'\xee', 239: b'\xef', 240: b'\xf0', 241: b'\xf1', 242: b'\xf2', 243: b'\xf3', 244: b'\xf4', 245: b'\xf5', 246: b'\xf6', 247: b'\xf7', 248: b'\xf8', 249: b'\xf9', 250: b'\xfa', 251: b'\xfb', 252: b'\xfc', 253: b'\xfd', 254: b'\xfe', 255: b'\xff', 256: b'e ', 257: b's ', 258: b'in', 259: b'th', 260: b' a', 261: b'en', 262: b't ', 263: b'd ', 264: b'or', 265: b'the ', 266: b'to', 267: b'ar', 268: b're', 269: b'al', 270: b'is ', 271: b'te', 272: b'ti', 273: b'co', 274: b'of', 275: b'ta', 276: b'ac', 277: b' the ', 278: b'ing', 279: b'm '}
```

**Merge Rules obtained after 24 merges**
```
Merge pair (101, 32) and replace with new id 256
Merge pair (115, 32) and replace with new id 257
Merge pair (105, 110) and replace with new id 258
Merge pair (116, 104) and replace with new id 259
Merge pair (32, 97) and replace with new id 260
Merge pair (101, 110) and replace with new id 261
Merge pair (116, 32) and replace with new id 262
Merge pair (100, 32) and replace with new id 263
Merge pair (111, 114) and replace with new id 264
Merge pair (259, 256) and replace with new id 265
Merge pair (116, 111) and replace with new id 266
Merge pair (97, 114) and replace with new id 267
Merge pair (114, 101) and replace with new id 268
Merge pair (97, 108) and replace with new id 269
Merge pair (105, 257) and replace with new id 270
Merge pair (116, 101) and replace with new id 271
Merge pair (116, 105) and replace with new id 272
Merge pair (99, 111) and replace with new id 273
Merge pair (111, 102) and replace with new id 274
Merge pair (116, 97) and replace with new id 275
Merge pair (97, 99) and replace with new id 276
Merge pair (32, 265) and replace with new id 277
Merge pair (258, 103) and replace with new id 278
Merge pair (109, 32) and replace with new id 279
```
After training the BBPE tokenizer, we will obtain a set of merge rules and a vocabulary, those two things will be stored and used for any future encoding and decoding tasks. 

### 3. Conclusion

In this post, we have gone through the BBPE tokenizer with many details. Let's quickly recap what we have done so far:

In order to understand why BBPE tokenizer is a popular choice for LLMs, we have checked other types of tokenizer, such as word-level tokenizer, character-level tokenizer, or byte level using UTF-8 directly. All of those tokenizers have their own advantage, but when used in the LLMs task, they all lack some key factors.

On the other hand, the BBPE tokenizer starts with a very small base vocabulary but also provides the flexibility to add new vocabulary by merging frequently appeared pairs. So the LLMs research can find a good balance between the good size of vocabulary and the good size of encoded tokens. This is the one advantage BBPE tokenizer can provide while other methods lack.

Then, we went through the initial BPE algorithm, and the byte-level implementation step by step. To train a BBPE tokenizer, all training texts will be encoded into raw bytes first (normally in UTF-8). Next, we will perform the BPE algorithm to find the most frequently appeared pairs to merge. We will repeat this step until we reach the desired vocabulary size. Finally, we will create the final vocabulary dictionary and all merge rules. Those two things will be stored for future encoding and decoding tasks.

For more details about this project, please visit my Kaggle notebook [What is BBPE -- Tokenizer behind LLMs](https://www.kaggle.com/code/binfeng2021/computer-vision-yolov8-on-traffic-detection)
