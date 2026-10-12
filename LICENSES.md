# 资源授权

`assets/character.glb` 由 `scripts/build-character.mjs` 生成，来源：

- Quaternius **Universal Animation Library**（UAL1、UAL2，Standard 版）：人体模型和大部分动作。授权 CC0 1.0。
  下载自 GitHub 镜像 NafisRayan/Animate-Rigged-Humanoid-No-Blender（附 Quaternius 的 License.txt）。
- **Mesh2Motion** 动作包（human-addon-animations.glb）：侧滑步、后退步、闪躲（用作蹬跨）、格斗准备姿势、三点着地、握拳庆祝、跪地喘气。
  美术资源授权 CC0，见 scottpetrovic/mesh2motion-app。

`data/shuttleset-ms-stats.json` 是从 ShuttleSet（Wang et al., KDD 2023，wywyWang/CoachAI-Projects）男单比赛逐拍数据统计出来的汇总数字（回球转移比例、各类击球的结束率），只含统计结果，不含原始数据。

## 音效（`assets/audio/`）

全部来自 Freesound，用的是网站上公开的 HQ 试听版（128 kbps mp3），由 `scripts/audio/prepare-sfx.mjs` 裁剪、转单声道、归一音量。除特别注明外授权都是 **CC0 1.0**，不需要署名，这里记下来方便查源头。

| 文件 | 用途 | 来源 |
|---|---|---|
| `hit-bright` | 杀球、扑球 | [Badminton.wav](https://freesound.org/people/PerMagnusLindborg/sounds/324244/) · PerMagnusLindborg |
| `hit-dry-1…6` | 主击球（暗的给吊球、网前，亮的给杀球、平抽） | [01_Badminton-6.wav](https://freesound.org/people/16HPanskaResatko_Matej/sounds/497962/) · 16HPanskaResatko_Matej |
| `hit-hall` | 高远球 | [Badminton hit.WAV](https://freesound.org/people/14FPanskaBubik_Lukas/sounds/418533/) · 14FPanskaBubik_Lukas |
| `hit-room-1…4` | 重球叠加的球馆混响层 | [Badminton.wav](https://freesound.org/people/13FPanska_Marval_Lukas/sounds/379325/) · 13FPanska_Marval_Lukas |
| `swish` | 杀球挥拍破风 | [SWSH_Badminton Racquet_Recording_03](https://freesound.org/people/JW_Audio/sounds/838769/) · JW_Audio |
| `squeak-1…4` | 急停、跨步的鞋声 | [sneaker squeak rubber.wav](https://freesound.org/people/shakaharu/sounds/88502/) · shakaharu |
| `squeak-5…8` | 急停、跨步的鞋声 | [30 Sneaker Squeaks.wav](https://freesound.org/people/adegenerate/sounds/71224/) · adegenerate |
| `scuff-1…5` | 启动蹬地 | [sneaker_skid.wav](https://freesound.org/people/shakaharu/sounds/68247/) · shakaharu |
| `crowd-hall` | 观众底噪（循环） | [Sports Hall Ambience, Walla](https://freesound.org/people/Kinoton/sounds/506454/) · Kinoton |
| `crowd-big` | 关键分时加大的人声（循环） | [Large_crowd_medium_distance_stereo.wav](https://freesound.org/people/eguobyte/sounds/360703/) · eguobyte |
| `wow-1…6` | 精彩球时轻声的「哦——啊——」 | [Crowd Ooohs and Ahhhs in Excitement](https://freesound.org/people/noah0189/sounds/264499/) · noah0189 |
| `cheer-big` | 赢下一局、比赛 | [AF Crowd Cheer Natural Ending.wav](https://freesound.org/people/mglennsound/sounds/678541/) · mglennsound |
| `applause` | 礼貌掌声 | [applause-30-people-auditorium.wav](https://freesound.org/people/michaelbesaw/sounds/656691/) · michaelbesaw |
| `ooh` | 惜败球的「哦」 | [small crowd gasp shock surprise](https://freesound.org/people/HowardV/sounds/264376/) · HowardV |
## 裁判报分（`assets/umpire/`）

用 [Kokoro-82M](https://huggingface.co/hexgrad/Kokoro-82M)（模型授权 Apache 2.0）通过 [kokoro-onnx](https://github.com/thewh1teagle/kokoro-onnx)（MIT）离线生成的英式男声（bm_george）词块，生成脚本 `scripts/audio/gen-umpire.py`。合成语音，不是真人录音。

## 中文解说（`assets/commentary/`）

用 [Kokoro-82M-v1.1-zh](https://huggingface.co/hexgrad/Kokoro-82M-v1.1-zh)（模型授权 Apache 2.0，中文部分的训练数据是 LongMaoData 提供的专业录音）通过 [kokoro-onnx](https://github.com/thewh1teagle/kokoro-onnx)（MIT）离线生成的男声（zm_096）词块，中文转音素用 [misaki-fork[zh]](https://pypi.org/project/misaki-fork/)（Apache 2.0）。词块表在 `src/sim/say.ts`，生成脚本 `scripts/audio/gen-commentary.py`，处理脚本 `scripts/audio/prepare-commentary.mjs`。合成语音，不是真人录音。

选型（2026-10）：只考虑可以商用、生成的音频能随游戏发布的模型。对比了 MeloTTS-Chinese（MIT）：只有一个女声，同样三句解说的音高起伏（半音标准差）约 1.2，Whisper 识别有约两成的字听错；Kokoro v1.1-zh 的 45 个男声起伏在 2.3–6.1 之间、识别基本全对。zm_096 是起伏、发音清晰度、浊音比例、语速综合靠前的一个，音高中等（中位约 150 Hz）；想换声音改 `gen-commentary.py` 的参数重新生成即可。

## 球员头像照片（Wikimedia Commons / Flickr）

只用当赛季（或就是那项赛事）拍的照片，没有的版本用文字头像。裁剪、缩放成 160×160 的头像（assets/avatars/），由 scripts/avatars/prepare-avatars.mjs 按 data/avatars.json 的裁剪框生成。CC BY-SA 授权的照片，裁剪后的头像同样按 CC BY-SA 发布；CC BY 的按 CC BY 署名使用。

| 照片 | 作者 | 授权 | 拍摄 | 用于版本 |
|---|---|---|---|---|
| [Lin Dan.jpg](https://commons.wikimedia.org/wiki/File:Lin_Dan.jpg) | Tksteven | CC BY-SA 2.5 | 2008 | lin-dan-08 |
| [Badminton-lin dan.jpg](https://commons.wikimedia.org/wiki/File:Badminton-lin_dan.jpg) | Mayeres | CC BY-SA 3.0 | 2011 | lin-dan-11 |
| [Lin Dan Triumphs (7758831398).jpg](https://commons.wikimedia.org/wiki/File:Lin_Dan_Triumphs_(7758831398).jpg) | Antony Stanley from Gloucester, UK | CC BY-SA 2.0 | 2012 | lin-dan-12 |
| [Podium of the individual final of the badminton test event 2016 Rio.jpg](https://commons.wikimedia.org/wiki/File:Podium_of_the_individual_final_of_the_badminton_test_event_2016_Rio.jpg) | André Motta (rededoesporte.gov.br) | CC BY 3.0 | 2015 | lin-dan-15 |
| [Lin Dan photp (Cropped).jpg](https://commons.wikimedia.org/wiki/File:Lin_Dan_photp_(Cropped).jpg) | Idontknowwhatisit | CC BY-SA 4.0 | 2017 | lin-dan-17 |
| [Badminton-lee chong wei.jpg](https://commons.wikimedia.org/wiki/File:Badminton-lee_chong_wei.jpg) | Mayeres | CC BY-SA 3.0 | 2009 | lcw-09 |
| [Lee Chong Wei2012.jpg](https://commons.wikimedia.org/wiki/File:Lee_Chong_Wei2012.jpg) | Ian Patterson | CC BY 2.0 | 2012 | lcw-12 |
| [Yonex IFB 2013 - Eightfinal - Lee Chong Wei — Ajay Jayaram 07.jpg](https://commons.wikimedia.org/wiki/File:Yonex_IFB_2013_-_Eightfinal_-_Lee_Chong_Wei_%E2%80%94_Ajay_Jayaram_07.jpg) | Pierre-Yves Beaudouin | CC BY-SA 4.0 | 2013 | lcw-13 |
| [Lee Chong Wei Indonesia Open 2016.jpg](https://commons.wikimedia.org/wiki/File:Lee_Chong_Wei_Indonesia_Open_2016.jpg) | Griff88 | CC BY-SA 4.0 | 2016 | lcw-16 |
| [KevinCordon4.jpg](https://commons.wikimedia.org/wiki/File:KevinCordon4.jpg) | Moy180 | CC0 | 2011 | cordon-11 |
| [Jan O Jorgensen Indonesia Open 2016.jpg](https://commons.wikimedia.org/wiki/File:Jan_O_Jorgensen_Indonesia_Open_2016.jpg) | Griff88 | CC BY-SA 4.0 | 2016 | jorgensen-16 |
| [Ayush Shetty Taipei Open 2025.jpg](https://commons.wikimedia.org/wiki/File:Ayush_Shetty_Taipei_Open_2025.jpg) | Tony2803.tw | CC BY 4.0 | 2025 | ayush-25 |
| [Ayush Shetty - Indonesia Open 2026.jpg](https://commons.wikimedia.org/wiki/File:Ayush_Shetty_-_Indonesia_Open_2026.jpg) | Griff88 | CC BY-SA 4.0 | 2026 | ayush-26 |
| [Kento Momota from Japan cropped (1).jpg](https://commons.wikimedia.org/wiki/File:Kento_Momota_from_Japan_cropped_(1).jpg) | Nardisoero (original photo), UCinternational (crop) | CC BY-SA 4.0 | 2019 | momota-19 |
| [Shi Yuqi - Indonesia Open 2018.jpg](https://commons.wikimedia.org/wiki/File:Shi_Yuqi_-_Indonesia_Open_2018.jpg) | Fauzi Ananta | CC BY 4.0 | 2018 | shi-yuqi-18 |
| [Badminton-wilson swiss open 2010-chen jin.jpg](https://commons.wikimedia.org/wiki/File:Badminton-wilson_swiss_open_2010-chen_jin.jpg) | Mayeres | CC BY-SA 3.0 | 2010 | chen-jin-10 |
| [Kunlavut Vitidsarn Indonesia Masters 2025.jpg](https://commons.wikimedia.org/wiki/File:Kunlavut_Vitidsarn_Indonesia_Masters_2025.jpg) | Jurnal Bulutangkis | CC BY 3.0 | 2025 | kunlavut-25 |
| [Badminton-lee hyun il cropped.jpg](https://commons.wikimedia.org/wiki/File:Badminton-lee_hyun_il_cropped.jpg) | Mayeres | CC BY-SA 3.0 | 2008 | lhi-08 |
| [Chou Tien-Chen (TPE) 2018.jpg](https://commons.wikimedia.org/wiki/File:Chou_Tien-Chen_(TPE)_2018.jpg) | Chartlin | CC BY-SA 4.0 | 2018 | chou-18 |
| [2019 Chinese Taipei Open 33.jpg](https://commons.wikimedia.org/wiki/File:2019_Chinese_Taipei_Open_33.jpg) | De-Shao Liu (Terry850324) | CC BY-SA 4.0 | 2019 | chou-19 |
| [US Open Badminton 2011 2822.jpg](https://commons.wikimedia.org/wiki/File:US_Open_Badminton_2011_2822.jpg) | Sunny Wan from Union City | CC BY 2.0 | 2011 | sasaki-11 |
| [Victor Lai - Indonesia Open 2026.jpg](https://commons.wikimedia.org/wiki/File:Victor_Lai_-_Indonesia_Open_2026.jpg) | Griff88 | CC BY-SA 4.0 | 2026 | victor-lai-26 |
| [Anthony Sinisuka Ginting - Indonesia Masters 2018.jpg](https://commons.wikimedia.org/wiki/File:Anthony_Sinisuka_Ginting_-_Indonesia_Masters_2018.jpg) | Fauziananta | CC BY 4.0 | 2018 | ginting-18 |
| [Alex Lanier 2026.jpg](https://commons.wikimedia.org/wiki/File:Alex_Lanier_2026.jpg) | De Reinal | CC0 | 2026 | lanier-26 |
| [Loh Kean Yew.jpg](https://commons.wikimedia.org/wiki/File:Loh_Kean_Yew.jpg) | Nardisoero | CC BY-SA 4.0 | 2021 | loh-21 |
| [Lee Chong Wei at the 2008 Olympic games.jpg](https://commons.wikimedia.org/wiki/File:Lee_Chong_Wei_at_the_2008_Olympic_games.jpg) | Dmitry Portnyagin (en:User:Дима) | CC BY-SA 3.0 | 2008-08-15 | lcw-08 |
| [Badminton (Flickr 3590034170)](https://www.flickr.com/photos/77516834@N00/3590034170) | Tom Thai (Flickr: eviltomthai) | CC BY 2.0 | 2008-08-15 | chen-jin-08 |
| [Épreuve Badminton Jeux Olympiques 2024 Arena Porte Chapelle - Paris XVIII (FR75) - 2024-07-28 - 21.jpg](https://commons.wikimedia.org/wiki/File:%C3%89preuve_Badminton_Jeux_Olympiques_2024_Arena_Porte_Chapelle_-_Paris_XVIII_(FR75)_-_2024-07-28_-_21.jpg) | Chabe01 | CC BY-SA 4.0 | 2024-07-28 | antonsen-24 |
| [Badminton 2012 Olympics.jpg](https://commons.wikimedia.org/wiki/File:Badminton_2012_Olympics.jpg) | Chris Eason | CC BY 2.0 | 2012-08-03 | lhi-12 |
| [Sho Sasaki (Flickr 7851869754)](https://www.flickr.com/photos/83996619@N04/7851869754) | M.o.B 68 (Flickr: MB3cky68) | CC BY-SA 2.0 | 2012-08-02 | sasaki-12 |
| [Blitzers ceremony photo.jpg](https://commons.wikimedia.org/wiki/File:Blitzers_ceremony_photo.jpg) | SPOTV Media Pte Ltd | CC BY-SA 4.0 | 2024-11-03 | kunlavut-24 |
| [2022 Taipei Open final round 03.jpg](https://commons.wikimedia.org/wiki/File:2022_Taipei_Open_final_round_03.jpg) | 總統府 / Office of the President, Taiwan (photo by Simon Liu) | CC BY 2.0 | 2022-07-24 | chou-22 |
