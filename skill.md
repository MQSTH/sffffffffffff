---
name: literasi-bahasa-inggris
description: >
  Gunakan skill ini saat pengguna menyebut "literasi bahasa inggris", "soal literasi", 
  "latihan TOBK", "latihan UTBK", "latihan inggris", "minta soal inggris", atau 
  frasa serupa yang menandakan ingin latihan soal Literasi Bahasa Inggris. 
  Skill ini membuat 20 soal pilihan ganda berbasis teks bacaan autentik,
  mencakup semua tipe soal TOBK/UTBK, dan menyajikannya sebagai widget interaktif 
  tertanam langsung di chat dengan timer hitung mundur 20 menit (1.200 detik), 
  sistem skoring otomatis, dan pembahasan lengkap di akhir.
---
 
# Literasi Bahasa Inggris — TOBK/UTBK Practice
 
## Overview
 
Skill ini membuat **widget interaktif tertanam di chat** (bukan file download) berupa ujian 20 soal Literasi Bahasa Inggris selama 20 menit. Setiap kali dipanggil, buat soal **baru yang berbeda** (jangan ulangi soal yang sama).
 
---
 
## Format Soal Autentik UTBK
 
Format asli UTBK Literasi Bahasa Inggris adalah:
- **3–4 teks bacaan panjang** (300–450 kata per teks)
- Setiap teks diikuti oleh **5–7 soal** yang mengacu ke teks tersebut
- Total 20 soal
- Soal **tidak punya passage sendiri-sendiri** — semuanya merujuk ke teks bacaan bersama
> ⚠️ **JANGAN buat soal dengan mini-passage per soal.** Teks bacaan ditampilkan sekali di atas, lalu soal-soal menyusul. Ini format asli UTBK.
 
---
 
## Cakupan Tipe Soal
 
Distribusikan 20 soal dari tipe-tipe berikut (variasikan tiap sesi):
 
| Tipe Soal | Jumlah Target |
|---|---|
| Tone / Attitude | 2–3 soal |
| Field of Study | 1–2 soal |
| Target Readers / The Writer | 1–2 soal |
| Vocabulary (Synonym / Antonym / Modal) | 2–3 soal |
| Reference (Pronoun rujukan) | 2–3 soal |
| Restatement | 2–3 soal |
| Summary / Main Idea | 2–3 soal |
| Analogy | 1–2 soal |
| Author's Positive Attitude | 1–2 soal |
| Irrelevant Sentence | 1–2 soal |
| Where Specific Info is Found | 1–2 soal |
 
---
 
## Materi Konten (Pengetahuan Inti)
 
### PAKET III — COURSE OF READING
- **Popular** (Magazine, Newspaper, Website): bahasa sederhana, topik umum → Target Readers: general readers / society. Tone: Informative, Objective, Neutral.
- **Specific** (Journal, Research Paper): bahasa ilmiah, topik sains → Target Readers: scientist, researcher, doctor. Tone: Informative, Objective, Resourceful.
- **Tone Highlight Fact** (Report, News, Explanation) → Informative, Objective, Neutral, Resourceful
- **Tone Highlight Opinion** (Argumentative, Hortatory, Discussion) → Subjective, Concerned, Worried, Critical, Persuasive
- **Email Thread Rumus THE KING = IS3**: Informative, Subjective, Supportive, Suggestive
### PAKET IV — VOCABULARY, REFERENCE, RESTATEMENT, SUMMARY
- Modal meanings: Can/Could=Ability, May/Might=Possibility, Shall/Should=Suggestion, Must/Had to=Obligation, Will/Would=Planning
- Reference: Subject (I/You/They/We/He/She/It), Object (Me/You/Them/Us/Him/Her/It), Possessive Adj (My/Your/Their/Our/His/Her/Its), Possessive Pron (Mine/Yours/Theirs/Ours/His/Hers/Its)
- Summary Rumus: **THE KING MADE LUSI** → MADE=Main Idea, LUSI=Conclusion
### PAKET V — ANALOGY, IRRELEVANT SENTENCE, WHERE INFO IS FOUND
- Analogy: baca paragraf yang berisi analogi → pilih opsi yang hubungannya paling mirip
- Author's Positive Attitude: cari pernyataan positif yang mendukung topik
- Irrelevant Sentence: kalimat yang tidak selaras dengan main idea (biasanya paragraph 1)
- Where Info is Found: temukan keyword dari pertanyaan, lalu cari di paragraf berapa
---
 
## Cara Membuat Soal
 
1. Buat **3–4 teks bacaan** dalam bahasa Inggris, **masing-masing 300–450 kata**. Topik akademik/umum: sains, lingkungan, teknologi, sosial, kesehatan. Variasikan genre (artikel populer, jurnal ilmiah, editorial, email thread).
2. Setiap teks menghasilkan **5–7 soal** dari tipe yang berbeda-beda.
3. Total soal = 20.
4. Setiap soal: **5 pilihan (A–E)**, satu jawaban benar.
5. Tentukan kunci jawaban (index 0–4) dan buat pembahasan singkat tiap soal.
---
 
## Struktur Data JavaScript
 
### Array `passages`
 
Buat array `passages` berisi semua teks bacaan:
 
```javascript
const passages = [
  {
    id: 0,
    label: "Text 1",           // label singkat
    genre: "Scientific Article", // genre teks
    text: `Paragraf penuh teks bacaan 1 di sini. 300–450 kata.
Gunakan template literal agar bisa multiline.
Bisa dibagi paragraf dengan \n\n.`
  },
  {
    id: 1,
    label: "Text 2",
    genre: "Opinion Editorial",
    text: `Teks bacaan 2 di sini...`
  },
  // dst...
];
```
 
### Array `Qs`
 
Setiap soal **tidak punya field `passage`** — ganti dengan `passageId` (index ke array `passages`):
 
```javascript
const Qs = [
  {
    passageId: 0,              // merujuk ke passages[0]
    cat: "Tone / Attitude",   // tipe soal
    q: "What is the tone of the text?",
    opts: ["A. Informative and objective","B. Subjective and critical","C. Persuasive and worried","D. Neutral and suggestive","E. Concerned and resourceful"],
    ans: 0,                   // index jawaban benar (0–4)
    exp: "Penjelasan singkat mengapa A benar."
  },
  // soal berikutnya...
];
```
 
> **Catatan penting**: opsi A–E ditulis langsung di dalam string (contoh: `"A. Informative and objective"`), bukan tanpa huruf. Ini lebih mirip format UTBK asli.
 
---
 
## Format Output: Inline Widget (visualize:show_widget)
 
**WAJIB** gunakan tool `visualize:show_widget` — BUKAN file HTML / `present_files`. Widget muncul langsung di chat.
 
Sebelum memanggil `show_widget`, panggil dulu `visualize:read_me` dengan module `["interactive"]` secara diam-diam.
 
### Struktur Widget
 
Widget berisi satu `<style>`, satu `<div id="qw">`, dan satu `<script>`. Semua inline, tanpa CDN eksternal.
 
#### Fitur Wajib Widget
- **Timer 20 menit (1.200 detik)** hitung mundur di pojok kanan atas.
- **Teks bacaan penuh** tampil di atas soal — bukan mini snippet. Teks panjang dibuat scrollable (max-height + overflow-y: auto).
- **Label passage** ("Text 1 — Scientific Article") tampil di atas teks.
- **Soal navigasi satu per satu** dengan dot navigator.
- **5 pilihan (A–E)** per soal dengan huruf lingkaran.
- **Tombol Prev / Skip / Next** untuk navigasi.
- **Submit confirm** di soal terakhir.
- **Halaman hasil**: skor, grade, pesan, stats, breakdown per kategori, tombol "Review jawaban" & "Coba lagi".
- **Review mode**: setelah submit, review semua soal dengan highlight benar/salah + penjelasan.
#### Perilaku Passage di Widget
 
Saat `renderQ()` dipanggil:
- Ambil `passages[Qs[cur].passageId]`
- Tampilkan label passage + teks penuh di atas soal
- Jika soal berturutan share passage yang sama, teks tetap ditampilkan (tidak perlu disembunyikan)
- Teks passage di-render dalam div scrollable agar tidak terlalu panjang halaman
#### Template CSS
 
```css
* { box-sizing: border-box; margin: 0; padding: 0; }
#qw { font-family: var(--font-sans, system-ui, sans-serif); padding: 1rem 0; max-width: 720px; }
.top-bar { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; }
.prog-bar { height: 3px; background: var(--color-border-tertiary, #E2E8F0); border-radius: 2px; margin-bottom: 1.25rem; }
.prog-fill { height: 100%; background: var(--color-text-primary, #1E293B); border-radius: 2px; transition: width 0.3s; }
.badge { font-size: 11px; color: var(--color-text-secondary, #64748B); background: var(--color-background-secondary, #F8FAFC); border: 0.5px solid var(--color-border-tertiary, #E2E8F0); border-radius: 20px; padding: 3px 10px; }
.timer-box { display: flex; align-items: center; gap: 6px; font-size: 13px; font-weight: 500; color: var(--color-text-secondary, #64748B); }
.timer-box.warn { color: #D85A30; }
.nav-dots { display: flex; flex-wrap: wrap; gap: 5px; margin-bottom: 1.25rem; }
.dot { width: 26px; height: 26px; border-radius: 50%; border: 0.5px solid var(--color-border-tertiary, #E2E8F0); background: var(--color-background-primary, #fff); font-size: 10px; font-weight: 500; cursor: pointer; display: flex; align-items: center; justify-content: center; color: var(--color-text-secondary, #64748B); transition: all 0.15s; }
.dot.active { background: var(--color-text-primary, #1E293B); color: var(--color-background-primary, #fff); border-color: var(--color-text-primary, #1E293B); }
.dot.done-correct { background: #E1F5EE; border-color: #1D9E75; color: #085041; }
.dot.done-wrong { background: #FAECE7; border-color: #D85A30; color: #4A1B0C; }
.dot.skipped { background: var(--color-background-secondary, #F8FAFC); border-style: dashed; }
 
/* Passage styles */
.passage-wrap { background: var(--color-background-secondary, #F8FAFC); border: 0.5px solid var(--color-border-tertiary, #E2E8F0); border-radius: 10px; padding: 14px 16px; margin-bottom: 1.25rem; }
.passage-label { font-size: 10px; color: var(--color-text-tertiary, #94A3B8); text-transform: uppercase; letter-spacing: .07em; font-weight: 600; margin-bottom: 8px; }
.passage-text { font-size: 14px; color: var(--color-text-secondary, #64748B); line-height: 1.8; max-height: 260px; overflow-y: auto; padding-right: 4px; }
.passage-text p { margin-bottom: 0.75em; }
.passage-text p:last-child { margin-bottom: 0; }
 
.q-area { margin-bottom: 1rem; }
.q-meta { font-size: 11px; color: var(--color-text-tertiary, #94A3B8); text-transform: uppercase; letter-spacing: .05em; margin-bottom: 6px; }
.q-text { font-size: 15px; color: var(--color-text-primary, #1E293B); line-height: 1.65; margin-bottom: 1.25rem; font-weight: 500; }
.opts { display: flex; flex-direction: column; gap: 8px; }
.opt { background: var(--color-background-primary, #fff); border: 0.5px solid var(--color-border-tertiary, #E2E8F0); border-radius: 10px; padding: 11px 14px; cursor: pointer; font-size: 14px; color: var(--color-text-primary, #1E293B); text-align: left; display: flex; gap: 10px; align-items: flex-start; transition: all 0.12s; font-family: inherit; }
.opt:hover:not(:disabled) { background: var(--color-background-secondary, #F8FAFC); border-color: var(--color-border-secondary, #CBD5E1); }
.opt-letter { width: 20px; min-width: 20px; height: 20px; border-radius: 50%; border: 0.5px solid var(--color-border-secondary, #CBD5E1); display: flex; align-items: center; justify-content: center; font-size: 11px; font-weight: 500; color: var(--color-text-secondary, #64748B); margin-top: 1px; flex-shrink: 0; }
.opt.selected .opt-letter { background: var(--color-text-primary, #1E293B); color: var(--color-background-primary, #fff); border-color: var(--color-text-primary, #1E293B); }
.opt.selected { border-color: var(--color-border-primary, #CBD5E1); }
.opt.correct { border-color: #1D9E75; background: #E1F5EE; }
.opt.correct .opt-letter { background: #1D9E75; color: #fff; border-color: #1D9E75; }
.opt.wrong { border-color: #D85A30; background: #FAECE7; }
.opt.wrong .opt-letter { background: #D85A30; color: #fff; border-color: #D85A30; }
.opt:disabled { cursor: default; }
.exp-box { margin-top: 10px; padding: 11px 13px; background: var(--color-background-secondary, #F8FAFC); border-radius: 8px; font-size: 13px; color: var(--color-text-secondary, #64748B); line-height: 1.6; border-left: 2px solid #1D9E75; }
.bottom-nav { display: flex; gap: 8px; margin-top: 1.25rem; align-items: center; }
.btn-nav { background: transparent; border: 0.5px solid var(--color-border-secondary, #CBD5E1); border-radius: 8px; padding: 9px 16px; font-size: 13px; cursor: pointer; font-family: inherit; color: var(--color-text-primary, #1E293B); }
.btn-nav:hover { background: var(--color-background-secondary, #F8FAFC); }
.btn-primary { background: var(--color-text-primary, #1E293B); color: var(--color-background-primary, #fff); border: none; border-radius: 8px; padding: 9px 18px; font-size: 13px; cursor: pointer; font-family: inherit; margin-left: auto; }
.btn-primary:hover { opacity: 0.85; }
.btn-skip { font-size: 12px; color: var(--color-text-tertiary, #94A3B8); background: none; border: none; cursor: pointer; font-family: inherit; padding: 9px 0; }
.btn-skip:hover { color: var(--color-text-secondary, #64748B); }
/* result styles */
.result-wrap { padding: 1rem 0; }
.r-top { display: flex; align-items: flex-end; gap: 12px; margin-bottom: 4px; }
.r-score-big { font-size: 64px; font-weight: 500; line-height: 1; color: var(--color-text-primary, #1E293B); }
.r-of { font-size: 18px; color: var(--color-text-tertiary, #94A3B8); margin-bottom: 10px; }
.r-grade { font-size: 16px; font-weight: 500; margin-bottom: 4px; }
.r-msg { font-size: 13px; color: var(--color-text-secondary, #64748B); margin-bottom: 1.5rem; }
.r-stats { display: grid; grid-template-columns: repeat(4, 1fr); gap: 10px; margin-bottom: 1.5rem; }
.r-stat { background: var(--color-background-secondary, #F8FAFC); border-radius: 8px; padding: 12px; text-align: center; }
.r-stat-val { font-size: 20px; font-weight: 500; color: var(--color-text-primary, #1E293B); }
.r-stat-lbl { font-size: 11px; color: var(--color-text-tertiary, #94A3B8); margin-top: 2px; }
.r-breakdown { margin-bottom: 1.5rem; }
.r-bd-title { font-size: 12px; color: var(--color-text-tertiary, #94A3B8); text-transform: uppercase; letter-spacing: .05em; margin-bottom: 10px; }
.r-bd-row { display: flex; justify-content: space-between; align-items: center; padding: 8px 0; border-bottom: 0.5px solid var(--color-border-tertiary, #E2E8F0); font-size: 13px; }
.r-bd-row:last-child { border-bottom: none; }
.r-bd-cat { color: var(--color-text-secondary, #64748B); }
.r-bd-score { font-weight: 500; }
.r-bd-bar-wrap { width: 80px; height: 4px; background: var(--color-border-tertiary, #E2E8F0); border-radius: 2px; }
.r-bd-bar { height: 100%; background: var(--color-text-primary, #1E293B); border-radius: 2px; }
.r-actions { display: flex; gap: 8px; }
.submit-confirm { background: var(--color-background-secondary, #F8FAFC); border: 0.5px solid var(--color-border-tertiary, #E2E8F0); border-radius: 10px; padding: 1.5rem; text-align: center; margin-bottom: 1rem; }
.sc-title { font-size: 16px; font-weight: 500; margin-bottom: 8px; }
.sc-sub { font-size: 13px; color: var(--color-text-secondary, #64748B); margin-bottom: 1.25rem; }
.sc-actions { display: flex; gap: 8px; justify-content: center; }
```
 
#### Template JS Lengkap
 
```javascript
// passages array dan Qs array di sini (lihat struktur data di atas)
 
let cur = 0, answers = new Array(Qs.length).fill(null);
let revealed = new Array(Qs.length).fill(false);
let totalSec = 1200, timerInt, quizDone = false;
 
function buildDots() {
  const wrap = document.getElementById('nav-dots'); wrap.innerHTML = '';
  Qs.forEach((_, i) => {
    const d = document.createElement('div');
    d.className = 'dot' + (i === cur ? ' active' : '');
    if (answers[i] !== null && revealed[i]) d.classList.add(answers[i] === Qs[i].ans ? 'done-correct' : 'done-wrong');
    else if (answers[i] !== null) d.classList.add('answered');
    d.textContent = i + 1;
    d.onclick = () => { if (!quizDone) goTo(i); };
    wrap.appendChild(d);
  });
}
 
function renderQ() {
  const q = Qs[cur];
  const p = passages[q.passageId];
  document.getElementById('q-badge').textContent = `Question ${cur+1} of ${Qs.length}`;
  document.getElementById('prog-fill').style.width = `${(cur/Qs.length)*100}%`;
  buildDots();
  const letters = ['A','B','C','D','E'];
 
  // Render passage
  const passageHTML = `<div class="passage-wrap">
    <div class="passage-label">${p.label} &mdash; ${p.genre}</div>
    <div class="passage-text">${p.text.replace(/\n\n/g,'</p><p>').replace(/^/,'<p>').replace(/$/,'</p>')}</div>
  </div>`;
 
  let html = passageHTML;
  html += `<div class="q-meta">${q.cat}</div>`;
  html += `<div class="q-text">${q.q.replace(/\n/g,'<br>')}</div><div class="opts">`;
  q.opts.forEach((o, i) => {
    let cls = 'opt';
    if (answers[cur] === i) cls += ' selected';
    if (revealed[cur]) {
      if (i === q.ans) cls += ' correct';
      else if (answers[cur] === i) cls += ' wrong';
    }
    html += `<button class="${cls}" onclick="selectOpt(${i})" ${revealed[cur]||quizDone?'disabled':''}>
      <span class="opt-letter">${letters[i]}</span><span>${o}</span></button>`;
  });
  html += '</div>';
  if (revealed[cur]) html += `<div class="exp-box">💡 ${q.exp}</div>`;
  document.getElementById('q-area').innerHTML = html;
  document.getElementById('btn-prev').style.display = cur === 0 ? 'none' : '';
  document.getElementById('btn-next').textContent = cur === Qs.length-1 ? 'Submit' : 'Next';
}
 
function selectOpt(i) { if (revealed[cur]||quizDone) return; answers[cur]=i; renderQ(); }
function skipQ() { if (cur<Qs.length-1) goTo(cur+1); }
function goTo(i) { if(i<0||i>=Qs.length) return; cur=i; document.getElementById('submit-confirm').style.display='none'; renderQ(); }
 
function handleNext() {
  if (cur < Qs.length-1) { goTo(cur+1); return; }
  const u = answers.filter(a=>a===null).length;
  document.getElementById('sc-sub-text').textContent = u>0
    ? `Masih ada ${u} soal belum dijawab. Submit sekarang?`
    : 'Semua soal sudah dijawab. Lihat hasil?';
  const sub = document.getElementById('submit-confirm');
  sub.style.display='block'; sub.scrollIntoView({behavior:'smooth'});
}
 
function finalSubmit() {
  clearInterval(timerInt); quizDone=true;
  revealed=new Array(Qs.length).fill(true); showResult();
}
 
function startTimer() {
  timerInt = setInterval(()=>{
    totalSec--;
    const m=Math.floor(totalSec/60), s=totalSec%60;
    const el=document.getElementById('timer-el');
    if(el) document.getElementById('timer-txt').textContent=`${String(m).padStart(2,'0')}:${String(s).padStart(2,'0')}`;
    if(totalSec<=120&&el) el.className='timer-box warn';
    if(totalSec<=0){clearInterval(timerInt);finalSubmit();}
  },1000);
}
 
function showResult() {
  document.getElementById('quiz-screen').style.display='none';
  const rs=document.getElementById('result-screen'); rs.style.display='block';
  const correct=answers.filter((a,i)=>a===Qs[i].ans).length;
  const wrong=answers.filter((a,i)=>a!==null&&a!==Qs[i].ans).length;
  const skipped=answers.filter(a=>a===null).length;
  const pct=Math.round(correct/Qs.length*100);
  const cats={};
  Qs.forEach((q,i)=>{if(!cats[q.cat])cats[q.cat]={correct:0,total:0};cats[q.cat].total++;if(answers[i]===q.ans)cats[q.cat].correct++;});
  let grade,msg;
  if(pct>=90){grade='Excellent';msg='Luar biasa — UTBK-ready!';}
  else if(pct>=75){grade='Proficient';msg='Hasil bagus. Asah kategori lemah dan kamu siap!';}
  else if(pct>=60){grade='Developing';msg='Fondasi solid. Fokus ke grammar dan inference.';}
  else{grade='Perlu Latihan';msg='Ulangi materi dan coba lagi. Konsistensi adalah kunci.';}
  let bdRows='';
  Object.entries(cats).forEach(([cat,d])=>{
    const p2=Math.round(d.correct/d.total*100);
    bdRows+=`<div class="r-bd-row"><span class="r-bd-cat">${cat}</span><div style="display:flex;align-items:center;gap:10px"><div class="r-bd-bar-wrap"><div class="r-bd-bar" style="width:${p2}%"></div></div><span class="r-bd-score">${d.correct}/${d.total}</span></div></div>`;
  });
  rs.innerHTML=`<div class="result-wrap">
    <div class="r-top"><div class="r-score-big">${correct}</div><div class="r-of">/ 20 benar</div></div>
    <div class="r-grade">${grade}</div><div class="r-msg">${msg}</div>
    <div class="r-stats">
      <div class="r-stat"><div class="r-stat-val">${correct}</div><div class="r-stat-lbl">Benar</div></div>
      <div class="r-stat"><div class="r-stat-val">${wrong}</div><div class="r-stat-lbl">Salah</div></div>
      <div class="r-stat"><div class="r-stat-val">${skipped}</div><div class="r-stat-lbl">Dilewat</div></div>
      <div class="r-stat"><div class="r-stat-val">${pct}%</div><div class="r-stat-lbl">Skor</div></div>
    </div>
    <div class="r-breakdown"><div class="r-bd-title">Breakdown per kategori</div>${bdRows}</div>
    <div class="r-actions">
      <button class="btn-nav" onclick="reviewAnswers()">Review jawaban</button>
      <button class="btn-primary" onclick="restartQuiz()">Coba lagi</button>
    </div>
  </div>`;
}
 
function reviewAnswers() {
  document.getElementById('quiz-screen').style.display='block';
  document.getElementById('result-screen').style.display='none';
  document.getElementById('bottom-nav').style.display='none';
  document.getElementById('submit-confirm').style.display='none';
  cur=0; renderQ();
}
 
function restartQuiz() {
  cur=0; answers=new Array(Qs.length).fill(null);
  revealed=new Array(Qs.length).fill(false);
  totalSec=1200; quizDone=false;
  document.getElementById('quiz-screen').style.display='block';
  document.getElementById('result-screen').style.display='none';
  document.getElementById('bottom-nav').style.display='flex';
  document.getElementById('submit-confirm').style.display='none';
  const te=document.getElementById('timer-el'); if(te) te.className='timer-box';
  clearInterval(timerInt); startTimer(); renderQ();
}
 
startTimer(); renderQ();
```
 
#### HTML Skeleton Widget
 
```html
<style>/* CSS template di atas */</style>
<div id="qw">
  <div id="quiz-screen">
    <div class="top-bar">
      <span class="badge" id="q-badge">Question 1 of 20</span>
      <div class="timer-box" id="timer-el">
        <svg width="13" height="13" viewBox="0 0 13 13" fill="none">
          <circle cx="6.5" cy="6.5" r="5.5" stroke="currentColor" stroke-width="1"/>
          <path d="M6.5 3.5V6.5L8.5 8" stroke="currentColor" stroke-width="1" stroke-linecap="round"/>
        </svg>
        <span id="timer-txt">20:00</span>
      </div>
    </div>
    <div class="prog-bar"><div class="prog-fill" id="prog-fill"></div></div>
    <div class="nav-dots" id="nav-dots"></div>
    <div class="q-area" id="q-area"></div>
    <div id="submit-confirm" class="submit-confirm" style="display:none">
      <div class="sc-title">Submit sekarang?</div>
      <div class="sc-sub" id="sc-sub-text"></div>
      <div class="sc-actions">
        <button class="btn-nav" onclick="document.getElementById('submit-confirm').style.display='none'">Kembali</button>
        <button class="btn-primary" onclick="finalSubmit()">Submit</button>
      </div>
    </div>
    <div class="bottom-nav" id="bottom-nav">
      <button class="btn-nav" id="btn-prev" onclick="goTo(cur-1)">Prev</button>
      <button class="btn-skip" onclick="skipQ()">Skip</button>
      <button class="btn-primary" id="btn-next" onclick="handleNext()">Next</button>
    </div>
  </div>
  <div id="result-screen" style="display:none"></div>
</div>
<script>/* JS template di atas — isi passages[] dan Qs[] dengan konten baru */</script>
```
 
---
 
## Instruksi Tambahan
 
- Setelah widget di-render, tambahkan pesan singkat di chat: *"20 soal siap! Timer langsung jalan. Selamat mengerjakan! 💪"*
- Jika pengguna meminta pembahasan tambahan setelah ujian, jelaskan strategi tipe soal yang bersangkutan menggunakan materi dari seksi Materi Konten di atas.
- Variasikan topik teks dan soal di setiap sesi agar tidak monoton.
- **INGAT**: selalu 5 opsi (A–E), index jawaban 0–4, gunakan `show_widget` bukan file HTML.
- **INGAT**: teks bacaan HARUS panjang (300–450 kata). Jangan buat teks pendek/ringkas — ini soal autentik UTBK, bukan kuis santai.
