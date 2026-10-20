# Gazi-Punjab-Tailors-and-Clothing-Store
Gazi Punjab Tailors and Clothing Store
import os, zipfile, textwrap

base = "/mnt/data/gazi_punjab_website"
os.makedirs(base, exist_ok=True)
os.makedirs(os.path.join(base, "assets"), exist_ok=True)

html = r'''<!doctype html>
<html lang="hi">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#173b32">
<title>GAZI PUNJAB TAILORS AND CLOTHING STORE</title>
<meta name="description" content="पैंट-शर्ट, कोट-पैंट, सलवार सूट, सफारी सूट, लहंगा-चुनरी और स्कूल यूनिफॉर्म की सिलाई। कपड़ा भी उपलब्ध।">
<style>
:root{--green:#173b32;--gold:#e7b85c;--cream:#fffaf0;--ink:#202820;--muted:#637067;--white:#fff}
*{box-sizing:border-box}html{scroll-behavior:smooth}body{margin:0;font-family:system-ui,-apple-system,"Noto Sans Devanagari",Arial,sans-serif;color:var(--ink);background:var(--cream);line-height:1.6}
a{color:inherit}.wrap{width:min(1120px,92%);margin:auto}
header{background:var(--green);color:white;position:sticky;top:0;z-index:5;box-shadow:0 3px 15px #0002}
.nav{display:flex;align-items:center;justify-content:space-between;gap:18px;padding:13px 0}.brand{font-weight:900;line-height:1.2;letter-spacing:.3px}.brand small{display:block;font-weight:500;color:#f4dba6;font-size:.78rem;margin-top:4px}
nav{display:flex;gap:16px;flex-wrap:wrap}nav a{text-decoration:none;font-weight:650;font-size:.92rem}.hero{background:linear-gradient(125deg,#173b32 0%,#245b4a 62%,#8b6b35 100%);color:white;padding:66px 0 60px;overflow:hidden}
.hero-grid{display:grid;grid-template-columns:1.3fr .7fr;align-items:center;gap:32px}.eyebrow{color:#f4dba6;font-weight:800;letter-spacing:1.5px;text-transform:uppercase}.hero h1{font-size:clamp(2rem,5vw,3.6rem);line-height:1.12;margin:12px 0}.hero p{font-size:1.08rem;max-width:660px;color:#f3f6f2}.actions{display:flex;gap:12px;flex-wrap:wrap;margin-top:24px}.btn{display:inline-flex;align-items:center;justify-content:center;border:0;border-radius:999px;padding:12px 19px;font-weight:800;text-decoration:none;cursor:pointer}.btn-gold{background:var(--gold);color:#1c2b22}.btn-white{background:#fff;color:var(--green)}.hero-card{border:1px solid #ffffff55;background:#ffffff12;border-radius:24px;padding:25px;text-align:center;backdrop-filter:blur(4px)}.needle{font-size:4rem}.hero-card strong{display:block;font-size:1.25rem}.hero-card span{color:#f4dba6}
section{padding:56px 0}.section-head{text-align:center;margin:0 auto 28px;max-width:720px}.section-head h2{font-size:clamp(1.7rem,4vw,2.5rem);color:var(--green);margin:0 0 8px}.section-head p{color:var(--muted);margin:0}.features{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}.feature,.service,.order-box,.info-box{background:white;border:1px solid #e9e5d8;border-radius:18px;padding:20px;box-shadow:0 8px 24px #1b30220a}.feature .ico{font-size:2rem}.feature h3{margin:8px 0 4px;color:var(--green)}.services{background:#f3efdf}.service-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}.service{padding:0;overflow:hidden}.service-art{height:150px;display:grid;place-items:center;background:linear-gradient(135deg,#e6d7b7,#f8f0dc);font-size:4.3rem}.service-body{padding:17px}.service h3{color:var(--green);margin:0 0 6px}.service p{margin:0 0 13px;color:var(--muted);font-size:.95rem}.mini-link{color:#17694d;font-weight:800;text-decoration:none}
.school{background:var(--green);color:white}.school h2{color:#f4dba6}.school p{color:#edf4ef}.school .btn{margin-top:8px}.order-grid{display:grid;grid-template-columns:1.1fr .9fr;gap:22px;align-items:start}.order-box h3,.info-box h3{color:var(--green);margin-top:0}.form-grid{display:grid;grid-template-columns:1fr 1fr;gap:13px}.field{display:flex;flex-direction:column;gap:5px}.field.full{grid-column:1/-1}label{font-weight:750;font-size:.92rem}input,select,textarea{font:inherit;padding:11px 12px;border:1px solid #d5d8ce;border-radius:10px;background:#fff;width:100%}textarea{min-height:88px;resize:vertical}.hint{font-size:.84rem;color:var(--muted)}.checkline{display:flex;gap:9px;align-items:flex-start}.checkline input{width:auto;margin-top:7px}.notice{background:#fff5dc;border-left:4px solid var(--gold);padding:12px 14px;border-radius:8px;font-size:.92rem;margin:15px 0}.contact{background:#f3efdf}.contact-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}.contact a{color:#17694d;font-weight:750}.contact .info-box p{margin:6px 0}.footer{background:#102b24;color:#e9f0e9;padding:26px 0;text-align:center}.footer p{margin:5px}.whatsapp-float{position:fixed;bottom:18px;right:18px;background:#168c50;color:white;text-decoration:none;border-radius:999px;padding:13px 17px;font-weight:900;box-shadow:0 6px 22px #0003;z-index:10}
@media(max-width:760px){.nav{align-items:flex-start;flex-direction:column}.hero-grid,.order-grid{grid-template-columns:1fr}.hero{padding:45px 0}.hero-card{max-width:420px}.features,.service-grid,.contact-grid{grid-template-columns:1fr 1fr}nav{gap:12px}.form-grid{grid-template-columns:1fr}}
@media(max-width:480px){.features,.service-grid,.contact-grid{grid-template-columns:1fr}.hero h1{font-size:2.15rem}.whatsapp-float{right:10px;bottom:10px}}
</style>
</head>
<body>
<header><div class="wrap nav">
  <div class="brand">GAZI PUNJAB TAILORS<small>AND CLOTHING STORE</small></div>
  <nav aria-label="मुख्य मेन्यू"><a href="#services">सेवाएँ</a><a href="#fabric">कपड़ा</a><a href="#order">ऑर्डर/नाप</a><a href="#contact">संपर्क</a></nav>
</div></header>
<main>
<section class="hero"><div class="wrap hero-grid">
 <div><div class="eyebrow">आपकी अपनी टेलरिंग शॉप</div>
 <h1>स्टाइल, क्वालिटी और फिटिंग — एक ही जगह</h1>
 <p>पैंट-शर्ट, कोट-पैंट, सलवार सूट, सफारी सूट, लहंगा-चुनरी और स्कूल ड्रेस की सिलाई। अपनी पसंद का कपड़ा चुनें या अपना कपड़ा लेकर आएँ।</p>
 <div class="actions"><a class="btn btn-gold" href="#order">नाप देकर ऑर्डर करें</a><a class="btn btn-white" href="https://wa.me/918809711859?text=Namaste%20Gazi%20Punjab%20Tailors%2C%20mujhe%20silai%20ka%20order%20karna%20hai." target="_blank" rel="noopener">WhatsApp पर संपर्क करें</a></div>
 </div>
 <div class="hero-card"><div class="needle">🧵✂️</div><strong>जहाँ फिटिंग ही हमारी गारंटी है!</strong><p>उचित मूल्य • साफ़ सिलाई • आपकी पसंद</p><span>Proprietor: Md Ikbal</span></div>
</div></section>
<section><div class="wrap"><div class="section-head"><h2>हमारी खासियत</h2><p>आपकी ज़रूरत के अनुसार कपड़े और सिलाई की सुविधा।</p></div>
<div class="features">
 <article class="feature"><div class="ico">📏</div><h3>अपना नाप भेजें</h3><p>वेबसाइट पर जानकारी भरें और WhatsApp पर ऑर्डर का मैसेज भेजें।</p></article>
 <article class="feature"><div class="ico">🧵</div><h3>कपड़ा भी उपलब्ध</h3><p>दुकान से कपड़ा चुन सकते हैं या अपना कपड़ा लाकर सिलाई करवा सकते हैं।</p></article>
 <article class="feature"><div class="ico">🗓️</div><h3>डिलीवरी समय चुनें</h3><p>अपनी ज़रूरत के अनुसार समय बताएँ। समय की पुष्टि दुकान की उपलब्धता पर होगी।</p></article>
</div></div></section>
<section class="services" id="services"><div class="wrap"><div class="section-head"><h2>हमारी सिलाई सेवाएँ</h2><p>जिस कपड़े की सिलाई चाहिए, उसे चुनकर ऑर्डर फॉर्म में जानकारी भरें।</p></div>
<div class="service-grid">
 <article class="service"><div class="service-art">🤵</div><div class="service-body"><h3>कोट-पैंट</h3><p>फॉर्मल और खास मौकों के लिए फिटिंग के अनुसार सिलाई।</p><a class="mini-link" href="#order" data-garment="कोट-पैंट">इस सेवा को चुनें →</a></div></article>
 <article class="service"><div class="service-art">👔</div><div class="service-body"><h3>पैंट-शर्ट</h3><p>रोज़मर्रा, स्कूल या ऑफिस के लिए पैंट-शर्ट।</p><a class="mini-link" href="#order" data-garment="पैंट-शर्ट">इस सेवा को चुनें →</a></div></article>
 <article class="service"><div class="service-art">🥻</div><div class="service-body"><h3>सलवार सूट</h3><p>आपकी पसंद और नाप के अनुसार सलवार सूट।</p><a class="mini-link" href="#order" data-garment="सलवार सूट">इस सेवा को चुनें →</a></div></article>
 <article class="service"><div class="service-art">🧥</div><div class="service-body"><h3>सफारी सूट</h3><p>साफ़-सुथरी सिलाई और आरामदायक फिटिंग।</p><a class="mini-link" href="#order" data-garment="सफारी सूट">इस सेवा को चुनें →</a></div></article>
 <article class="service"><div class="service-art">👗</div><div class="service-body"><h3>लहंगा-चुनरी</h3><p>शादी और त्योहारों के लिए लहंगा-चुनरी की सिलाई।</p><a class="mini-link" href="#order" data-garment="लहंगा-चुनरी">इस सेवा को चुनें →</a></div></article>
 <article class="service"><div class="service-art">🎒</div><div class="service-body"><h3>स्कूल ड्रेस</h3><p>स्कूलों के लिए पैंट-शर्ट, स्कर्ट-शर्ट और सलवार सूट यूनिफॉर्म।</p><a class="mini-link" href="#order" data-garment="स्कूल ड्रेस">इस सेवा को चुनें →</a></div></article>
 <article class="service"><div class="service-art">🧣</div><div class="service-body"><h3>चुनरी</h3><p>आपकी पसंद के अनुसार चुनरी और संबंधित परिधान।</p><a class="mini-link" href="#order" data-garment="चुनरी">इस सेवा को चुनें →</a></div></article>
 <article class="service"><div class="service-art">🪡</div><div class="service-body"><h3>अन्य सिलाई</h3><p>किसी अन्य कपड़े की सिलाई के लिए विवरण लिखें।</p><a class="mini-link" href="#order" data-garment="अन्य सिलाई">इस सेवा को चुनें →</a></div></article>
</div></div></section>
<section id="fabric"><div class="wrap"><div class="section-head"><h2>कपड़ा भी हमारे यहाँ उपलब्ध</h2><p>अब सिलाई के साथ कपड़ा चुनने की सुविधा भी।</p></div>
<div class="features">
 <article class="feature"><div class="ico">🛍️</div><h3>दुकान से कपड़ा लें</h3><p>पैंट-शर्ट, कोट-पैंट और अन्य परिधानों के लिए कपड़े की उपलब्धता व कीमत WhatsApp पर पूछें।</p><a class="mini-link" href="https://wa.me/918809711859?text=Namaste%2C%20mujhe%20dukaan%20par%20available%20kapde%20aur%20price%20ki%20jaankari%20chahiye." target="_blank" rel="noopener">कपड़े की जानकारी लें →</a></article>
 <article class="feature"><div class="ico">🧺</div><h3>अपना कपड़ा लाएँ</h3><p>ग्राहक बाहर से लाया हुआ कपड़ा भी सिलाई के लिए दे सकते हैं।</p><a class="mini-link" href="#order" data-fabric="अपना कपड़ा लाऊँगा/लाऊँगी">अपना कपड़ा चुनें →</a></article>
 <article class="feature"><div class="ico">💬</div><h3>उचित मूल्य</h3><p>कपड़े और सिलाई की अंतिम कीमत ऑर्डर की जानकारी देखने के बाद बताई जाएगी।</p></article>
</div></div></section>
<section class="school"><div class="wrap"><div class="section-head"><h2>स्कूल यूनिफॉर्म के ऑर्डर लिए जाते हैं</h2><p>अगर आप स्कूल चलाते हैं और बच्चों के लिए स्कूल ड्रेस बनवाना चाहते हैं, तो Gazi Punjab Tailors and Clothing Store से ज़रूर संपर्क करें। यहाँ उचित मूल्य पर अच्छी क्वालिटी की स्कूल ड्रेस तैयार की जाती है। पैंट-शर्ट, स्कर्ट-शर्ट और सलवार सूट यूनिफॉर्म के लिए संपर्क करें।</p><a class="btn btn-gold" href="https://wa.me/918809711859?text=Namaste%2C%20humein%20school%20uniform%20ka%20bulk%20order%20aur%20rate%20ki%20jaankari%20chahiye." target="_blank" rel="noopener">स्कूल ड्रेस का ऑर्डर पूछें</a></div></div></section>
<section id="order"><div class="wrap"><div class="section-head"><h2>ऑनलाइन नाप और ऑर्डर फॉर्म</h2><p>जानकारी भरें, फिर WhatsApp पर भेजें। फ़ॉर्म भेजना अपने-आप ऑर्डर की पुष्टि नहीं है।</p></div>
<div class="order-grid"><div class="order-box"><h3>अपनी जानकारी भरें</h3>
<form id="orderForm"><div class="form-grid">
<div class="field"><label for="name">ग्राहक का नाम *</label><input id="name" required placeholder="अपना नाम"></div>
<div class="field"><label for="phone">मोबाइल नंबर *</label><input id="phone" required inputmode="tel" placeholder="आपका नंबर"></div>
<div class="field"><label for="garment">कपड़े का प्रकार *</label><select id="garment" required><option value="">कपड़ा चुनें</option><option>कोट-पैंट</option><option>पैंट-शर्ट</option><option>सलवार सूट</option><option>सफारी सूट</option><option>लहंगा-चुनरी</option><option>चुनरी</option><option>स्कूल ड्रेस</option><option>अन्य सिलाई</option></select></div>
<div class="field"><label for="fabricChoice">कपड़ा कहाँ से लेंगे? *</label><select id="fabricChoice" required><option value="">विकल्प चुनें</option><option>दुकान से कपड़ा चाहिए</option><option>अपना कपड़ा लाऊँगा/लाऊँगी</option><option>पहले कीमत/कपड़ा पूछना है</option></select></div>
<div class="field"><label for="quantity">कितने कपड़े/सेट?</label><input id="quantity" type="number" min="1" value="1"></div>
<div class="field"><label for="delivery">डिलीवरी का समय *</label><select id="delivery" required><option>7 दिन</option><option>48 घंटे (उपलब्धता की पुष्टि ज़रूरी)</option><option>3 दिन</option><option>15 दिन</option><option>अपनी तारीख</option></select></div>
<div class="field"><label for="date">अपनी डिलीवरी तारीख (यदि लागू)</label><input id="date" type="date"></div>
<div class="field"><label for="price">बजट/कीमत (वैकल्पिक)</label><input id="price" placeholder="यदि कोई बजट हो"></div>
<div class="field full"><label for="measurements">नाप का विवरण *</label><textarea id="measurements" required placeholder="उदाहरण: लंबाई, छाती, कमर, हिप, बाजू, कंधा आदि। जो नाप लागू हो, लिखें।"></textarea><div class="hint">अलग-अलग कपड़ों के नाप अलग होते हैं। ज़रूरी नाप और कोई खास निर्देश यहाँ लिखें।</div></div>
<div class="field full"><label for="notes">अन्य निर्देश</label><textarea id="notes" placeholder="डिज़ाइन, रंग, स्कूल/संस्था का नाम या अन्य जानकारी"></textarea></div>
<div class="field full checkline"><input id="urgent" type="checkbox"><label for="urgent">मेरा ऑर्डर अर्जेंट है — कृपया उपलब्धता की पुष्टि करें।</label></div>
<div class="field full"><button class="btn btn-gold" type="submit">WhatsApp पर नाप और ऑर्डर भेजें</button></div>
</div></form><div class="notice">महत्वपूर्ण: 48 घंटे या किसी भी चुने हुए समय की डिलीवरी दुकान की क्षमता, कपड़े की उपलब्धता, नाप और कीमत की पुष्टि पर निर्भर है। आपकी ओर से पुष्टि मिलने के बाद ही ऑर्डर पक्का होगा।</div>
</div>
<aside class="info-box"><h3>ऑर्डर कैसे होगा?</h3><p><b>1.</b> कपड़ा और नाप की जानकारी भरें।</p><p><b>2.</b> WhatsApp बटन दबाकर मैसेज भेजें।</p><p><b>3.</b> दुकान की ओर से कीमत, कपड़े की उपलब्धता और डिलीवरी समय की पुष्टि होगी।</p><p><b>4.</b> आपकी पुष्टि के बाद ही ऑर्डर कन्फर्म माना जाएगा।</p><hr><h3>ईमेल</h3><p><a href="mailto:gazipanjabtailorsgst@gmail.com">gazipanjabtailorsgst@gmail.com</a></p><p class="hint">यह शुरुआती वेबसाइट फॉर्म WhatsApp में मैसेज तैयार करता है। ईमेल पर अपने-आप नाप भेजने की सुविधा अलग फॉर्म सेवा जोड़ने पर सक्रिय होगी।</p></aside>
</div></div></section>
<section class="contact" id="contact"><div class="wrap"><div class="section-head"><h2>संपर्क और दुकान का पता</h2><p>ऑर्डर, कपड़े की उपलब्धता और स्कूल यूनिफॉर्म की जानकारी के लिए संपर्क करें।</p></div>
<div class="contact-grid">
<div class="info-box"><h3>📞 मोबाइल / WhatsApp</h3><p><a href="tel:+918809711859">8809711859</a></p><p><a href="tel:+919546580400">9546580400</a></p><p><a href="https://wa.me/918809711859" target="_blank" rel="noopener">WhatsApp पर संदेश भेजें</a></p></div>
<div class="info-box"><h3>📍 दुकान का पता</h3><p>Gazi Punjab Tailors and Clothing Store</p><p>Barsoi Bazar, Dhaan Hatti Road, Sultanpur, Barsoi, Katihar, Bihar 855102, India</p></div>
<div class="info-box"><h3>🏪 व्यवसाय विवरण</h3><p><b>Proprietor:</b> Md Ikbal</p><p><b>GSTIN:</b> 10AJLPI3285K1Z6</p><p><b>ईमेल:</b> <a href="mailto:gazipanjabtailorsgst@gmail.com">gazipanjabtailorsgst@gmail.com</a></p></div>
</div></div></section>
</main>
<footer class="footer"><div class="wrap"><p><b>GAZI PUNJAB TAILORS AND CLOTHING STORE</b></p><p>जहाँ फिटिंग ही हमारी गारंटी है!</p><p>© <span id="year"></span> Gazi Punjab Tailors and Clothing Store</p></div></footer>
<a class="whatsapp-float" href="https://wa.me/918809711859?text=Namaste%20Gazi%20Punjab%20Tailors" target="_blank" rel="noopener" aria-label="WhatsApp पर संपर्क करें">WhatsApp</a>
<script>
document.getElementById('year').textContent = new Date().getFullYear();
document.querySelectorAll('[data-garment]').forEach(el=>el.addEventListener('click',()=>{document.getElementById('garment').value=el.dataset.garment}));
document.querySelectorAll('[data-fabric]').forEach(el=>el.addEventListener('click',()=>{document.getElementById('fabricChoice').value=el.dataset.fabric}));
document.getElementById('orderForm').addEventListener('submit',function(e){
 e.preventDefault();
 const v=id=>document.getElementById(id).value.trim();
 const urgent=document.getElementById('urgent').checked?'हाँ':'नहीं';
 const msg=[
 'नमस्ते Gazi Punjab Tailors and Clothing Store, मुझे सिलाई/कपड़े का ऑर्डर देना है।',
 'नाम: '+v('name'),'मोबाइल: '+v('phone'),'कपड़े का प्रकार: '+v('garment'),
 'कपड़ा: '+v('fabricChoice'),'मात्रा: '+(v('quantity')||'1'),'डिलीवरी समय: '+v('delivery'),
 'अपनी तारीख: '+(v('date')||'नहीं चुनी'),'बजट/कीमत: '+(v('price')||'बात करके तय करेंगे'),
 'नाप: '+v('measurements'),'अर्जेंट ऑर्डर: '+urgent,'अन्य निर्देश: '+(v('notes')||'कोई नहीं'),
 'कृपया कीमत, कपड़े की उपलब्धता और डिलीवरी समय की पुष्टि करें। आपकी पुष्टि के बाद ही ऑर्डर कन्फर्म होगा।'
 ].join('\\n');
 window.open('https://wa.me/918809711859?text='+encodeURIComponent(msg),'_blank','noopener');
});
</script>
</body></html>'''

with open(os.path.join(base, "index.html"), "w", encoding="utf-8") as f:
    f.write(html)

readme = """GAZI PUNJAB TAILORS AND CLOTHING STORE — Website starter

Files:
- index.html: responsive Hindi website with services, fabric choices, order/measurement form, WhatsApp ordering, school-uniform information, contact and GST details.

How to test:
1. Open index.html in a browser.
2. Fill the order form and press “WhatsApp पर नाप और ऑर्डर भेजें”. It opens WhatsApp with a pre-filled order message.
3. Before publishing, review the address and GSTIN carefully.

Free hosting with GitHub Pages:
1. Sign in or create a GitHub account.
2. Create a new public repository (for example: gazi-punjab-tailors).
3. Upload index.html to the repository root and commit.
4. Open Settings → Pages; under Build and deployment choose Deploy from a branch, select main and /(root), then Save.
5. Wait for GitHub Pages to show the published URL.

Important:
- The current form sends the order message to WhatsApp (it does not automatically email measurement details).
- Orders are NOT automatically confirmed. The shop must confirm price, fabric availability, and delivery time.
- The garment icons are placeholders. Replace them with actual garment photos, and add the shop logo/signboard images, when those image files are available.
- WhatsApp currently opens a message to 8809711859. The second number is shown in contact details.
"""
with open(os.path.join(base, "README.txt"), "w", encoding="utf-8") as f:
    f.write(readme)

zip_path = "/mnt/data/gazi_punjab_tailors_website.zip"
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    for root, dirs, files in os.walk(base):
        for name in files:
            p = os.path.join(root, name)
            z.write(p, os.path.relpath(p, base))

print("Website files created:")
print("/mnt/data/gazi_punjab_website/index.html")
print("/mnt/data/gazi_punjab_website/README.txt")
print(zip_path)
