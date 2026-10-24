# pro-launch

[English](README.md) | [简体中文](README.zh-CN.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Tiếng Việt](README.vi.md) | हिन्दी

<p align="center"><img src="docs/share.png" alt="pro-launch: from an idea to style frames" width="100%"></p>
<p align="center"><sub><a href="https://github.com/jack-reson8/copy-that"><b>Copy That</b></a> सीरीज़ का हिस्सा · एक लाइन में पूरा सेट इंस्टॉल करें</sub></p>

यह Claude Code का एक skill है जो किसी प्रोडक्ट को 0 से 1 तक **टेस्ट-फ़र्स्ट** तरीके से ले जाता है: पोज़िशनिंग → नाम, डोमेन और ट्रेडमार्क → रेफ़रेंस खोज (पहले GitHub/ओपन-सोर्स, फिर App Store और अवॉर्ड विजेता) → स्टाइल बाइबल → फ़ीचर मैप → UI/UX बिल्ड लूप → असेट जनरेशन → असली डिवाइस पर QA → लॉन्च वीडियो → GTM → ग्रोथ → ओपन-सोर्स / App Store पर शिप।

यह क्यों बना: AI से बने ज़्यादातर प्रोडक्ट कोड की वजह से नहीं, बल्कि इन वजहों से फ़ेल होते हैं: (1) असली रेफ़रेंस कभी स्टडी नहीं किए गए, (2) मॉडल अपने ही काम को खुद नंबर देता है, (3) यूज़र के बार-बार दिए गए सुधार कहीं लिखे नहीं जाते। इसलिए यहाँ हर चरण में **असली आर्टिफ़ैक्ट** बनाना ज़रूरी है और अगला चरण शुरू होने से पहले एक **गेट** (`scripts/phase_gate.py`) पास करना पड़ता है।

## इंस्टॉल

Claude Code में:

```
/plugin marketplace add jack-reson8/pro-launch
/plugin install pro-launch@pro-launch
```

या सादे skill फ़ोल्डर के रूप में:

```bash
git clone https://github.com/jack-reson8/pro-launch /tmp/pro-launch && cp -R /tmp/pro-launch/plugins/pro-launch/skills/pro-launch ~/.claude/skills/
```
फिर Claude Code से कहें, जैसे: "मेरे लिए एक ऐप बनाओ", "यह UI बहुत आम लग रहा है", "रेफ़रेंस ढूँढो", "इस प्रोडक्ट का नाम सुझाओ", "लॉन्च की योजना बनाओ"।

**Codex** (CLI या ChatGPT डेस्कटॉप ऐप):

```bash
codex plugin marketplace add jack-reson8/pro-launch
codex plugin add pro-launch@pro-launch
```

या `plugins/pro-launch/skills/pro-launch` को `~/.codex/skills/` में कॉपी करें। यह skill ओपन [Agent Skills](https://agentskills.io) स्टैंडर्ड का पालन करता है, इसलिए Claude Code, Codex और SKILL.md पढ़ने वाले हर एजेंट में चलता है।

**अन्य एजेंट** (Cursor, Gemini CLI, GitHub Copilot और skills CLI द्वारा सपोर्ट किए जाने वाले दूसरे एजेंट):

```bash
npx skills add jack-reson8/pro-launch
```

## अंदर क्या है

skill `plugins/pro-launch/skills/pro-launch` में है; नीचे के सभी पाथ इसी फ़ोल्डर के सापेक्ष हैं।

- `SKILL.md` – चरण, गेट और अटल नियम
- `references/01-13` – हर चरण का एक पेज (कई देशों में लॉन्च के लिए ट्रेडमार्क और IP सहित)
- `references/mistakes.md`, `user-repeated-demands.md` – असली गलतियों का बही-खाता और यूज़र की बार-बार दोहराई जाने वाली माँगें
- `scripts/` – फ़ेज़ गेट, App Store पोस्टर डाउनलोडर, रेफ़रेंस आर्काइवर, डोमेन / App Store नाम जाँच, कटआउट→वेक्टर पाइपलाइन (Vision + vtracer + svgo)
- `examples/`, `assets/` – व्यावहारिक उदाहरण और टेम्पलेट

MIT लाइसेंस। Claude Code skills के साथ काम करता है; यह तरीका दूसरे एजेंट पर भी लागू किया जा सकता है।
