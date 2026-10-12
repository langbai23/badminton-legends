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
