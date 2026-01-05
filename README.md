# Bengali-Oz-Spandan <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bengali Learning</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;}
body{
  font-family:'Noto Sans Bengali','Segoe UI',sans-serif;
  background:#f5f5f5;
  color:#333;
  display:flex;
  justify-content:center;
  padding:20px;
}
.container{
  max-width:900px;
  width:100%;
  background:#fff;
  padding:20px;
  border-radius:12px;
  box-shadow:0 6px 20px rgba(0,0,0,0.1);
}
.home, .lessons-container{margin-bottom:20px;}
button{
  padding:10px 20px;
  margin:5px 5px 15px 0;
  border:none;
  background:#007BFF;
  color:#fff;
  border-radius:8px;
  cursor:pointer;
  transition:0.2s;
  font-size:14px;
}
button:hover{background:#0056b3;}
.lesson{
  margin-bottom:15px;
  padding:15px;
  border-radius:10px;
  background:#fafafa;
  border:1px solid #ddd;
  cursor:pointer;
}
.lesson h3{color:#007BFF;margin-bottom:8px;}
.example{margin-bottom:6px;}
.q{font-weight:bold;color:#222;}
.translit{margin-left:15px;color:#007BFF;font-style:italic;}
.a{margin-left:15px;color:#555;}
.eng{margin-left:15px;font-style:italic;color:#555;}
</style>
</head>
<body>
<div class="container">

  <!-- Home Screen -->
  <div class="home" id="homeScreen">
    <h2>Welcome to Bengali Learning</h2>
    <p>Select a level to start learning:</p>
    <button data-level="beginner">Beginner Level</button>
    <button data-level="intermediate">Intermediate Level</button>
    <button data-level="advanced">Advanced Level</button>
  </div>

  <!-- Lessons Container -->
  <div class="lessons-container" id="lessonsContainer" style="display:none;"></div>

</div>

<script>
// ---------- Beginner Lessons (1–12) ----------
const beginnerLessons = [
{title:"Lesson 1: Pronouns",description:"Learn basic pronouns.",examples:[
{bengali:"আমি",translit:"Ami",english:"I"},
{bengali:"আমরা",translit:"Amra",english:"We"},
{bengali:"তুমি",translit:"Tumi",english:"You (informal)"},
{bengali:"আপনি",translit:"Apni",english:"You (formal)"},
{bengali:"সে",translit:"Se",english:"He / She"},
{bengali:"তারা",translit:"Tara",english:"They"}
]},
{title:"Lesson 2: Greetings",description:"Common greetings.",examples:[
{bengali:"হ্যালো",translit:"Hello",english:"Hello"},
{bengali:"নমস্কার",translit:"Nomoskar",english:"Greetings"},
{bengali:"ধন্যবাদ",translit:"Dhonnobad",english:"Thank you"},
{bengali:"দয়া করে",translit:"Doya kore",english:"Please"},
{bengali:"দুঃখিত",translit:"Dukkito",english:"Sorry"}
]},
{title:"Lesson 3: Numbers",description:"Numbers 1–10",examples:[
{bengali:"১",translit:"Ek",english:"One"},
{bengali:"২",translit:"Dui",english:"Two"},
{bengali:"৩",translit:"Tin",english:"Three"},
{bengali:"৪",translit:"Char",english:"Four"},
{bengali:"৫",translit:"Panch",english:"Five"},
{bengali:"৬",translit:"Chhoy",english:"Six"},
{bengali:"৭",translit:"Sat",english:"Seven"},
{bengali:"৮",translit:"Aṭ",english:"Eight"},
{bengali:"৯",translit:"Noy",english:"Nine"},
{bengali:"১০",translit:"Dosh",english:"Ten"}
]},
{title:"Lesson 4: Family",description:"Family members",examples:[
{bengali:"মা",translit:"Ma",english:"Mother"},
{bengali:"বাবা",translit:"Baba",english:"Father"},
{bengali:"ভাই",translit:"Bhai",english:"Brother"},
{bengali:"বোন",translit:"Bon",english:"Sister"}
]},
{title:"Lesson 5: Food",description:"Food & drinks",examples:[
{bengali:"ভাত",translit:"Bhat",english:"Rice"},
{bengali:"দুধ",translit:"Dudh",english:"Milk"},
{bengali:"জল",translit:"Jol",english:"Water"},
{bengali:"মাছ",translit:"Mach",english:"Fish"}
]},
{title:"Lesson 6: Verbs",description:"Daily verbs",examples:[
{bengali:"খাওয়া",translit:"Khaoa",english:"To eat"},
{bengali:"যাওয়া",translit:"Jaoya",english:"To go"},
{bengali:"আসা",translit:"Asa",english:"To come"},
{bengali:"ঘুমানো",translit:"Ghumano",english:"To sleep"}
]},
{title:"Lesson 7: Sentences",description:"Simple sentences",examples:[
{bengali:"আমি ভাত খাই।",translit:"Ami bhat khai",english:"I eat rice"},
{bengali:"তুমি কোথায় যাচ্ছো?",translit:"Tumi kothay jaccho?",english:"Where are you going?"}
]},
{title:"Lesson 8: Plurals",description:"Plural words",examples:[
{bengali:"আমরা",translit:"Amra",english:"We"},
{bengali:"তারা",translit:"Tara",english:"They"},
{bengali:"বন্ধুরা",translit:"Bondhura",english:"Friends"}
]},
{title:"Lesson 9: Colors",description:"Basic colors",examples:[
{bengali:"লাল",translit:"Lal",english:"Red"},
{bengali:"নীল",translit:"Nil",english:"Blue"},
{bengali:"সবুজ",translit:"Shobuj",english:"Green"},
{bengali:"হলুদ",translit:"Holud",english:"Yellow"}
]},
{title:"Lesson 10: Common Bengali Words",description:"Most commonly used Bengali words in daily life.",examples:[
{bengali:"হ্যাঁ",translit:"Hya",english:"Yes"},
{bengali:"না",translit:"Na",english:"No"},
{bengali:"ভালো",translit:"Bhalo",english:"Good"},
{bengali:"খারাপ",translit:"Kharap",english:"Bad"},
{bengali:"অনেক",translit:"Onek",english:"Many"},
{bengali:"একটু",translit:"Ektu",english:"A little"},
{bengali:"আজ",translit:"Aj",english:"Today"},
{bengali:"এখন",translit:"Ekhon",english:"Now"},
{bengali:"চাই",translit:"Chai",english:"Want"},
{bengali:"পারি",translit:"Pari",english:"Can"}
]},
{title:"Lesson 11: Question Words",description:"Learn how to ask questions in Bengali.",examples:[
{bengali:"কি",translit:"Ki",english:"What"},
{bengali:"কে",translit:"Ke",english:"Who"},
{bengali:"কোথায়",translit:"Kothay",english:"Where"},
{bengali:"কখন",translit:"Kokhon",english:"When"},
{bengali:"কেন",translit:"Keno",english:"Why"},
{bengali:"কিভাবে",translit:"Kibhabe",english:"How"},
{bengali:"কত",translit:"Koto",english:"How much / many"},
{bengali:"কোন",translit:"Kon",english:"Which"}
]},
{title:"Lesson 12: Daily Mini Conversations",description:"Short daily dialogues with transliteration.",examples:[
{q:"হ্যালো! তুমি কেমন আছো?",translit:"Hello! Tumi kemon acho?",a:"আমি ভালো আছি। তুমি কেমন?",translita:"Ami bhalo achi. Tumi kemon?",eng:"Hello! How are you? — I am fine. How about you?"},
{q:"তুমি কোথায় যাচ্ছো?",translit:"Tumi kothay jaccho?",a:"আমি বাজার যাচ্ছি।",translita:"Ami bazar jacchi.",eng:"Where are you going? — I am going to the market."}
]}
];

// ---------- Intermediate Lessons (13–20) ----------
const intermediateLessons = [
{title:"Lesson 13: Daily Activities",description:"Intermediate verbs & daily routines.",examples:[
{bengali:"স্নান করা",translit:"Snan kora",english:"To take a bath"},
{bengali:"খাবার তৈরি করা",translit:"Khabar toiri kora",english:"To prepare food"},
{bengali:"কাজ করা",translit:"Kaj kora",english:"To work"},
{bengali:"বাজারে যাওয়া",translit:"Bazar-e jaoya",english:"To go to market"}
]},
{title:"Lesson 14: Time Expressions",description:"Talking about time.",examples:[
{bengali:"আজ সকালে",translit:"Aj sokale",english:"This morning"},
{bengali:"বিকেলে",translit:"Bikale",english:"In the afternoon"},
{bengali:"রাতে",translit:"Rate",english:"At night"},
{bengali:"কাল",translit:"Kal",english:"Tomorrow / Yesterday"}
]},
{title:"Lesson 15: Weather",description:"Describing weather.",examples:[
{bengali:"সুন্দর আবহাওয়া",translit:"Sundor abohawa",english:"Nice weather"},
{bengali:"বৃষ্টি হচ্ছে",translit:"Brishti hochhe",english:"It's raining"},
{bengali:"তুষার পড়ছে",translit:"Tushar porchhe",english:"It's snowing"},
{bengali:"ঠাণ্ডা",translit:"Thanda",english:"Cold"}
]},
{title:"Lesson 16: Directions & Places",description:"Giving directions.",examples:[
{bengali:"সোজা যাও",translit:"Soja jao",english:"Go straight"},
{bengali:"বামে ঘোরো",translit:"Bame ghor-o",english:"Turn left"},
{bengali:"ডানে ঘোরো",translit:"Dane ghor-o",english:"Turn right"},
{bengali:"স্কুল",translit:"Skul",english:"School"},
{bengali:"হাসপাতাল",translit:"Hospital",english:"Hospital"}
]},
{title:"Lesson 17: Shopping",description:"Common shopping words.",examples:[
{bengali:"দোকান",translit:"Dokan",english:"Shop"},
{bengali:"মূল্য",translit:"Mulya",english:"Price"},
{bengali:"কম দাম",translit:"Kom dam",english:"Low price"},
{bengali:"কিনতে চাই",translit:"Kinte chai",english:"Want to buy"}
]},
{title:"Lesson 18: Health & Body",description:"Parts of body and health expressions.",examples:[
{bengali:"হাত",translit:"Hat",english:"Hand"},
{bengali:"পা",translit:"Pa",english:"Leg"},
{bengali:"মাথা",translit:"Matha",english:"Head"},
{bengali:"ব্যথা",translit:"Byatha",english:"Pain"},
{bengali:"ডাক্তার",translit:"Daktar",english:"Doctor"}
]},
{title:"Lesson 19: Travel & Transport",description:"Travel phrases.",examples:[
{bengali:"ট্রেন",translit:"Train",english:"Train"},
{bengali:"বাস",translit:"Bus",english:"Bus"},
{bengali:"ট্যাক্সি",translit:"Taxi",english:"Taxi"},
{bengali:"কীভাবে যাব?",translit:"Kibhabe jabo?",english:"How will I go?"}
]},
{title:"Lesson 20: Simple Conversations",description:"Intermediate mini dialogues.",examples:[
{q:"তুমি কোথায় যাচ্ছো?",translit:"Tumi kothay jaccho?",a:"আমি অফিস যাচ্ছি।",translita:"Ami office jacchi.",eng:"Where are you going? — I am going to the office."},
{q:"তুমি কি খেয়েছো?",translit:"Tumi ki kheyecho?",a:"হ্যাঁ, আমি খেয়েছি।",translita:"Hya, ami kheyechi.",eng:"Have you eaten? — Yes, I have eaten."}
]}
];

// ---------- Advanced Lessons (21–30) ----------
const advancedLessons = [
{title:"Lesson 21: Compound Sentences",description:"Learn to form compound sentences.",examples:[
{bengali:"আমি বাজারে যাচ্ছি এবং তুমি কি করছো?",translit:"Ami bazar-e jacchi ebong tumi ki korcho?",english:"I am going to the market and what are you doing?"}
]},
{title:"Lesson 22: Past Tense",description:"Talking about past events.",examples:[
{bengali:"আমি গতকাল সিনেমা দেখেছি।",translit:"Ami gotokal cinema dekhechi.",english:"I watched a movie yesterday."}
]},
{title:"Lesson 23: Future Tense",description:"Talking about future plans.",examples:[
{bengali:"আমি আগামীকাল স্কুল যাব।",translit:"Ami agamikal skul jabo.",english:"I will go to school tomorrow."}
]},
{title:"Lesson 24: Idioms",description:"Common Bengali idioms.",examples:[
{bengali:"নাকে দাগ পড়া",translit:"Nake dag pora",english:"To get embarrassed"},
{bengali:"চোখে ধুলা লাগা",translit:"Chokhe dhula laga",english:"To be blind to something"}
]},
{title:"Lesson 25: Proverbs",description:"Famous Bengali proverbs.",examples:[
{bengali:"যত বড় সমস্যা, তত বড় সমাধান",translit:"Joto boro shomossa, toto boro shomadhan",english:"Every problem has a solution"}
]},
{title:"Lesson 26: Storytelling",description:"Read & understand short stories.",examples:[
{bengali:"একবার একটি ছেলে ছিল...",translit:"Ekbar ekti chele chhilo...",english:"Once there was a boy..."}
]},
{title:"Lesson 27: Formal Speech",description:"Using polite/formal language.",examples:[
{bengali:"আপনি কেমন আছেন?",translit:"Apni kemon achhen?",english:"How are you? (formal)"}
]},
{title:"Lesson 28: Informal Speech",description:"Using casual language.",examples:[
{bengali:"তুমি কেমন আছো?",translit:"Tumi kemon achho?",english:"How are you? (informal)"}
]},
{title:"Lesson 29: Writing Letters",description:"Basic letter writing.",examples:[
{bengali:"প্রিয় বন্ধু,",translit:"Priyo bondhu,",english:"Dear friend,"}
]},
{title:"Lesson 30: Essay Writing",description:"Simple essays.",examples:[
{bengali:"আমার স্কুল জীবন",translit:"Amar skul jibon",english:"My school life"}
]}
];

// ---------- Render Lessons ----------
const homeScreen = document.getElementById("homeScreen");
const lessonsContainer = document.getElementById("lessonsContainer");

homeScreen.addEventListener("click",(e)=>{
  if(e.target.tagName==="BUTTON"){
    const level = e.target.getAttribute("data-level");
    let lessonsToShow = [];
    if(level==="beginner") lessonsToShow = beginnerLessons;
    else if(level==="intermediate") lessonsToShow = intermediateLessons;
    else if(level==="advanced") lessonsToShow = advancedLessons;

    homeScreen.style.display="none";
    lessonsContainer.style.display="block";
    renderLessons(lessonsToShow);
  }
});

function renderLessons(lessons){
  lessonsContainer.innerHTML="";

  // Home button
  const homeBtn = document.createElement("button");
  homeBtn.textContent="← Back to Home";
  homeBtn.style.background="#28a745";
  homeBtn.style.marginBottom="15px";
  homeBtn.addEventListener("click",()=>{
    lessonsContainer.style.display="none";
    homeScreen.style.display="block";
  });
  lessonsContainer.appendChild(homeBtn);

  lessons.forEach(lesson=>{
    const lessonDiv = document.createElement("div");
    lessonDiv.className="lesson";
    lessonDiv.innerHTML=`<h3>${lesson.title}</h3><p>${lesson.description}</p>`;

    lesson.examples.forEach(e=>{
      if(e.q){
        lessonDiv.innerHTML+=`
<div class="example">
<div class="q">Q: ${e.q}</div>
<div class="translit">(${e.translit})</div>
<div class="a">A: ${e.a}</div>
<div class="translit">(${e.translita})</div>
<div class="eng">(${e.eng})</div>
</div>`;
      }else{
        lessonDiv.innerHTML+=`
<div class="example">
<b>${e.bengali}</b> (${e.translit}) — ${e.english}
</div>`;
      }
    });
    lessonsContainer.appendChild(lessonDiv);
  });
}
</script>
</body>
</
