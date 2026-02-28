<script>

// INIT EMAILJS
(function(){
emailjs.init("63eS7AoUU_bR-VqJB");
})();

// HANTAR EMAIL
function sendNotification(question, answer){
emailjs.send("service_5b4v71w","template_4gz34mh",{
question: question,
answer: answer,
time: new Date().toLocaleString()
})
.then(function(response){
console.log("SUCCESS", response.status);
}, function(error){
console.log("FAILED", error);
});
}

// ANIMATION
function showContent(html){
const content=document.getElementById("content");
content.classList.remove("show");
content.classList.add("fade");

setTimeout(()=>{
content.innerHTML=html;
content.classList.remove("fade");
content.classList.add("show");
},300);
}

// UNIVERSAL BUTTON FUNCTION
function answerFlow(question, answer, nextPage){
sendNotification(question, answer);

if(nextPage){
nextPage();
}else{
showContent(`
<h2>Terima kasih 🤍</h2>
<p>Saya doakan awak sentiasa bahagia.</p>
`);
}
}

// PAGE 1
function start(){
showContent(`
<h2>Hi...</h2>
<p>Saya cuma nak tanya,<br>
awak sihat ke sekarang?<br>
Dah okay ke selepas semua ni?</p>

<button class="btn-primary" onclick="answerFlow(
'Awak sihat & dah okay?',
'Saya okay',
page2
)">Saya okay</button>

<button class="btn-secondary" onclick="answerFlow(
'Awak sihat & dah okay?',
'Belum sepenuhnya okay',
page2
)">Belum sepenuhnya okay</button>
`);
}

// PAGE 2
function page2(){
showContent(`
<h2>Sebelum saya teruskan...</h2>
<p>Saya nak minta maaf kalau mesej ni mengganggu awak.<br>
Saya cuma terlalu rindu dan masih belajar lepaskan.</p>

<button class="btn-primary" onclick="answerFlow(
'Adakah mesej ini mengganggu?',
'Tak mengganggu',
page3
)">Tak mengganggu, teruskan</button>

<button class="btn-secondary" onclick="answerFlow(
'Adakah mesej ini mengganggu?',
'Rasa tak sesuai',
null
)">Rasa tak sesuai</button>
`);
}

// PAGE 3
function page3(){
showContent(`
<h2>Kehidupan awak sekarang...</h2>
<p>Awak dah jumpa kawan baru ke sekarang?<br>
Hidup awak makin bahagia tanpa saya?</p>

<button class="btn-primary" onclick="answerFlow(
'Kehidupan sekarang',
'Ya, makin bahagia',
page4
)">Ya, makin bahagia</button>

<button class="btn-secondary" onclick="answerFlow(
'Kehidupan sekarang',
'Masih proses',
page4
)">Masih proses</button>
`);
}

// PAGE 4
function page4(){
showContent(`
<h2>Saya jujur...</h2>
<p>Saya cuba move on,<br>
tapi kadang kalah dengan kenangan sendiri.<br>
Awak dah betul-betul move on ke?</p>

<button class="btn-primary" onclick="answerFlow(
'Awak dah move on?',
'Ya',
page5
)">Ya</button>

<button class="btn-secondary" onclick="answerFlow(
'Awak dah move on?',
'Belum sepenuhnya',
page5
)">Belum sepenuhnya</button>
`);
}

// PAGE 5
function page5(){
showContent(`
<h2>Satu benda saya ternampak...</h2>
<p>Saya ada nampak awak follow IG Jama awak.<br>
Awak dah okay dan membaik sekarang?</p>

<button class="btn-primary" onclick="answerFlow(
'Adakah awak dah okay sekarang?',
'Ya, saya okay',
finalPage
)">Ya, saya okay</button>

<button class="btn-secondary" onclick="answerFlow(
'Adakah awak dah okay sekarang?',
'Tak pasti lagi',
finalPage
)">Tak pasti lagi</button>
`);
}

// FINAL
function finalPage(){
showContent(`
<h2>Soalan terakhir...</h2>
<p>Awak rasa bekas kekasih boleh jadi kawan?</p>

<button class="btn-primary" onclick="answerFlow(
'Boleh jadi kawan selepas jadi ex?',
'Ya boleh',
null
)">Ya, boleh</button>

<button class="btn-secondary" onclick="answerFlow(
'Boleh jadi kawan selepas jadi ex?',
'Tak sesuai',
null
)">Tak sesuai</button>
`);
}

start();

</script>
