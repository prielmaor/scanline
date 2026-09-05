<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SCANLINE — זיהוי חפצים ואיתור קנייה</title>
<style>
  :root{
    --bg:#0A0D10;
    --bg-2:#10151A;
    --panel:#12181D;
    --panel-2:#161D23;
    --line:#233038;
    --line-bright:#2FE6C0;
    --cyan:#2FE6C0;
    --cyan-dim:#1B8F76;
    --amber:#F0A93A;
    --red:#FF5A5A;
    --text:#E7EEF0;
    --text-dim:#7F8E94;
    --mono: ui-monospace, 'SF Mono', 'Menlo', 'Consolas', monospace;
    --sans: -apple-system, 'Segoe UI', Arial, sans-serif;
  }
  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;}
  body{
    background:
      radial-gradient(ellipse 900px 500px at 50% -10%, rgba(47,230,192,0.08), transparent 60%),
      repeating-linear-gradient(0deg, rgba(255,255,255,0.012) 0px, rgba(255,255,255,0.012) 1px, transparent 1px, transparent 3px),
      var(--bg);
    color:var(--text);
    font-family:var(--sans);
    min-height:100vh;
  }
  .wrap{max-width:920px;margin:0 auto;padding:28px 18px 90px;}

  header{
    display:flex; align-items:center; justify-content:space-between;
    padding-bottom:16px; margin-bottom:26px; border-bottom:1px solid var(--line);
    gap:14px; flex-wrap:wrap;
  }
  .brand{display:flex; align-items:center; gap:12px;}
  .brand-mark{
    width:38px;height:38px; border:1.5px solid var(--cyan); border-radius:8px;
    display:flex;align-items:center;justify-content:center; flex-shrink:0;
    color:var(--cyan); font-family:var(--mono); font-size:16px;
    box-shadow:0 0 14px rgba(47,230,192,0.35) inset;
  }
  .brand h1{
    font-size:19px; margin:0; letter-spacing:0.02em; font-weight:700;
  }
  .brand .tagline{font-family:var(--mono); font-size:11px; color:var(--text-dim); margin-top:2px; letter-spacing:0.03em;}
  .status-pill{
    font-family:var(--mono); font-size:11px; color:var(--cyan);
    border:1px solid var(--cyan-dim); border-radius:20px; padding:5px 12px;
    display:flex; align-items:center; gap:7px; white-space:nowrap;
  }
  .status-pill .led{width:7px;height:7px;border-radius:50%; background:var(--cyan); box-shadow:0 0 6px var(--cyan); animation:pulse 1.6s ease-in-out infinite;}
  @keyframes pulse{0%,100%{opacity:1;}50%{opacity:.35;}}

  .intro{font-size:14px; color:var(--text-dim); line-height:1.7; margin-bottom:22px; max-width:60ch;}

  /* Scanner / intake */
  .scanner{
    position:relative;
    background:var(--panel);
    border:1px solid var(--line);
    border-radius:10px;
    overflow:hidden;
    margin-bottom:10px;
  }
  .corner{position:absolute; width:22px; height:22px; z-index:2; pointer-events:none;}
  .corner.tl{top:10px; left:10px; border-top:2px solid var(--cyan); border-left:2px solid var(--cyan); border-radius:4px 0 0 0;}
  .corner.tr{top:10px; right:10px; border-top:2px solid var(--cyan); border-right:2px solid var(--cyan); border-radius:0 4px 0 0;}
  .corner.bl{bottom:10px; left:10px; border-bottom:2px solid var(--cyan); border-left:2px solid var(--cyan); border-radius:0 0 0 4px;}
  .corner.br{bottom:10px; right:10px; border-bottom:2px solid var(--cyan); border-right:2px solid var(--cyan); border-radius:0 0 4px 0;}

  .drop-label{
    display:block; padding:56px 20px; text-align:center; cursor:pointer;
    position:relative; z-index:1;
  }
  .drop-label.dragover{ background:rgba(47,230,192,0.06); }
  .drop-label .icon{
    width:52px; height:52px; margin:0 auto 16px; border:1.5px solid var(--line-bright);
    border-radius:50%; display:flex; align-items:center; justify-content:center;
    color:var(--cyan); font-size:22px;
  }
  .drop-label .main-txt{font-size:15.5px; font-weight:600;}
  .drop-label .sub-txt{font-family:var(--mono); font-size:11px; color:var(--text-dim); margin-top:8px; letter-spacing:0.03em;}
  input[type=file]{
    position:absolute; width:1px; height:1px; padding:0; margin:-1px;
    overflow:hidden; clip:rect(0,0,0,0); white-space:nowrap; border:0;
  }

  .crop-stage{ padding:16px; position:relative; z-index:1; }
  .crop-frame{
    position:relative; width:100%; overflow:hidden; border-radius:8px;
    touch-action:none; background:#000; border:1px solid var(--line);
  }
  .crop-frame img{ width:100%; height:auto; display:block; user-select:none; -webkit-user-drag:none; }
  .crop-box{
    position:absolute; border:2px dashed var(--cyan); background:rgba(47,230,192,0.15);
    box-shadow:0 0 0 2000px rgba(0,0,0,0.45); pointer-events:none;
  }
  .crop-hint{font-family:var(--mono); font-size:10.5px; color:var(--text-dim); margin-top:10px; letter-spacing:0.02em;}
  .crop-actions{display:flex; gap:8px; margin-top:12px; flex-wrap:wrap;}

  .preview-row{
    display:flex; align-items:center; gap:16px;
    padding:16px 20px; border-top:1px solid var(--line);
    background:var(--panel-2);
  }
  .preview-thumb{
    position:relative; width:72px; height:72px; flex-shrink:0; border-radius:6px; overflow:hidden;
    border:1px solid var(--line-bright);
  }
  .preview-thumb img{width:100%; height:100%; object-fit:cover; display:block;}
  .scanbar{
    position:absolute; left:0; right:0; height:2px; background:var(--cyan);
    box-shadow:0 0 8px var(--cyan); top:0; animation:scan 1.4s ease-in-out infinite;
    display:none;
  }
  .scanbar.active{display:block;}
  @keyframes scan{0%{top:0;}50%{top:calc(100% - 2px);}100%{top:0;}}

  .preview-meta{flex:1; min-width:0;}
  .preview-meta .fname{font-size:13.5px; font-weight:600; overflow:hidden; text-overflow:ellipsis; white-space:nowrap;}
  .preview-meta .fhint{font-family:var(--mono); font-size:10.5px; color:var(--text-dim); margin-top:4px; letter-spacing:0.02em;}

  .go-btn{
    background:var(--cyan); color:#05201A; border:none; border-radius:7px;
    font-family:var(--sans); font-weight:700; font-size:14.5px;
    padding:11px 20px; cursor:pointer; white-space:nowrap;
    box-shadow:0 0 16px rgba(47,230,192,0.35);
  }
  .go-btn:hover{filter:brightness(1.08);}
  .go-btn:disabled{background:#3A4147; color:var(--text-dim); cursor:not-allowed; box-shadow:none;}

  .caption-note{font-family:var(--mono); font-size:11px; color:var(--text-dim); margin:14px 2px 32px; line-height:1.8; letter-spacing:0.01em;}

  /* Filters */
  .filters{display:flex; gap:8px; flex-wrap:wrap; margin:26px 0 18px;}
  .chip{
    border:1px solid var(--line); background:transparent; border-radius:7px;
    padding:7px 13px; font-family:var(--mono); font-size:12px;
    cursor:pointer; color:var(--text-dim); font-weight:500; letter-spacing:0.01em;
    transition:all .12s ease;
  }
  .chip.active{background:rgba(47,230,192,0.12); border-color:var(--cyan); color:var(--cyan);}
  .filter-sep{width:1px; background:var(--line); align-self:stretch; margin:2px 2px;}

  .region-row{display:flex; align-items:center; gap:8px; margin-bottom:16px; flex-wrap:wrap;}
  .region-label{font-family:var(--mono); font-size:11px; color:var(--text-dim); letter-spacing:0.02em;}

  .refine-row{
    display:flex; gap:8px; align-items:center; margin:10px 0 4px; flex-wrap:wrap;
  }
  .refine-input{
    flex:1; min-width:160px; background:var(--bg-2); border:1px solid var(--line); border-radius:7px;
    color:var(--text); font-family:var(--sans); font-size:13.5px; padding:9px 12px;
  }
  .refine-input:focus{outline:none; border-color:var(--cyan);}
  .refine-btn{
    background:transparent; border:1px solid var(--cyan-dim); color:var(--cyan);
    border-radius:7px; font-family:var(--sans); font-weight:600; font-size:13px;
    padding:9px 14px; cursor:pointer; white-space:nowrap;
  }
  .refine-btn:hover{background:rgba(47,230,192,0.08);}
  .refine-btn:disabled{opacity:.5; cursor:not-allowed;}
  .refine-hint{font-family:var(--mono); font-size:10.5px; color:var(--text-dim); margin-top:6px;}

  /* Result header */
  .item-head{
    display:flex; gap:16px; align-items:flex-start;
    padding:18px; margin-bottom:6px; border:1px solid var(--line); border-radius:10px; background:var(--panel);
  }
  .item-head img{width:96px; height:96px; object-fit:cover; border-radius:7px; border:1px solid var(--line-bright); flex-shrink:0;}
  .item-head .eyebrow{font-family:var(--mono); font-size:10.5px; color:var(--cyan); letter-spacing:0.05em; margin-bottom:6px;}
  .item-head h2{font-size:20px; margin:0 0 8px; font-weight:700;}
  .item-head p{margin:0; font-size:13.5px; color:var(--text-dim); line-height:1.65;}
  .value-pill{
    display:inline-flex; align-items:center; gap:6px; margin-top:10px;
    font-family:var(--mono); font-size:12px; color:var(--amber);
    border:1px solid var(--amber); border-radius:6px; padding:5px 10px;
  }

  .status-line{
    display:flex; align-items:center; gap:10px;
    font-family:var(--mono); font-size:13px; color:var(--cyan); padding:20px 2px;
  }
  .spinner{
    width:13px;height:13px;border:2px solid var(--line); border-top-color:var(--cyan);
    border-radius:50%; animation:spin .7s linear infinite;
  }
  @keyframes spin{to{transform:rotate(360deg);}}

  .error-box{
    border:1px solid var(--red); background:rgba(255,90,90,0.08); color:var(--red);
    border-radius:8px; padding:14px 16px; font-size:13.5px; margin:18px 0;
  }

  /* Listing cards -- this is the primary payoff, so make it the visual focus */
  .listings{display:flex; flex-direction:column; gap:10px; margin-top:14px;}
  .listing{
    background:var(--panel); border:1px solid var(--line); border-radius:10px;
    padding:16px 18px; transition:border-color .12s ease;
  }
  .listing:hover{border-color:var(--line-bright);}
  .l-top{display:flex; justify-content:space-between; align-items:flex-start; gap:12px;}
  .l-seller{font-size:15px; font-weight:700;}
  .l-price{font-family:var(--mono); font-size:16px; font-weight:700; color:var(--cyan); white-space:nowrap;}
  .l-note{font-size:12.5px; color:var(--text-dim); margin-top:6px; line-height:1.6;}
  .l-tags{display:flex; gap:6px; margin-top:11px; flex-wrap:wrap;}
  .tag{
    font-family:var(--mono); font-size:10.5px; padding:3px 9px; border-radius:5px; border:1px solid; font-weight:600; letter-spacing:0.02em;
  }
  .tag.orig{color:var(--cyan); border-color:var(--cyan-dim); background:rgba(47,230,192,0.08);}
  .tag.replica{color:var(--red); border-color:var(--red); background:rgba(255,90,90,0.08);}
  .tag.unknown-type{color:var(--text-dim); border-color:var(--line);}
  .tag.trusted{color:var(--amber); border-color:var(--amber); background:rgba(240,169,58,0.08);}
  .tag.suspect{color:var(--red); border-color:var(--red); background:rgba(255,90,90,0.08);}
  .tag.unknown-trust{color:var(--text-dim); border-color:var(--line);}
  .tag.origin-tag{color:var(--text); border-color:var(--line);}

  .buy-btn{
    margin-top:13px; display:inline-flex; align-items:center; gap:7px;
    background:var(--cyan); color:#05201A; text-decoration:none;
    font-family:var(--sans); font-weight:700; font-size:13px;
    padding:9px 16px; border-radius:7px;
  }
  .buy-btn:hover{filter:brightness(1.08);}
  .buy-btn .arrow{font-size:14px;}
  .l-domain{font-family:var(--mono); font-size:10.5px; color:var(--text-dim); margin-top:8px; word-break:break-all;}

  .empty-state{
    text-align:center; padding:40px 20px; color:var(--text-dim); font-family:var(--mono); font-size:12.5px;
  }

  footer{margin-top:56px; padding-top:16px; border-top:1px solid var(--line); font-family:var(--mono); font-size:10.5px; color:var(--text-dim); text-align:center; letter-spacing:0.02em;}

  @media (max-width:560px){
    .item-head{flex-direction:column;}
    .item-head img{width:100%; height:170px;}
    .l-top{flex-direction:column; align-items:flex-start; gap:4px;}
  }
</style>
</head>
<body>
<div class="wrap">

  <header>
    <div class="brand">
      <div class="brand-mark">◎</div>
      <div>
        <h1>SCANLINE</h1>
        <div class="tagline">זיהוי חפצים · איתור מקורות קנייה</div>
      </div>
    </div>
    <div class="status-pill"><span class="led"></span>מוכן לסריקה</div>
  </header>

  <div class="intro">מצלמים או מעלים תמונה של חפץ — כל חפץ, מכל מקום, גם צילום מסך מתוך סרט — והמערכת מזהה אותו ומאתרת ברשת איפה בדיוק אפשר לקנות אותו, עם דירוג מקור/חיקוי ואמינות לכל מוכר.</div>

  <div class="region-row">
    <span class="region-label">// אזור חיפוש:</span>
    <button class="chip" id="israelToggle">🇮🇱 העדף מוכרים בישראל / משלוח לישראל</button>
  </div>

  <div class="scanner">
    <div class="corner tl"></div><div class="corner tr"></div>
    <div class="corner bl"></div><div class="corner br"></div>
    <label class="drop-label" id="dropZone">
      <div class="icon">⌖</div>
      <div class="main-txt">גררו תמונה, או הקישו לצילום / בחירה מהגלריה</div>
      <div class="sub-txt">JPG · PNG · WEBP</div>
      <input type="file" id="fileInput" accept="image/*">
    </label>
    <div class="crop-stage" id="cropStage" style="display:none;">
      <div class="crop-frame" id="cropFrame">
        <img id="cropImg" alt="בחרו אזור לחיתוך">
        <div class="crop-box" id="cropBox" style="display:none;"></div>
      </div>
      <div class="crop-hint">// גררו מלבן על החלק שרוצים לחדד (למשל: הפחית בתוך פריים מהסרט)</div>
      <div class="crop-actions">
        <button class="refine-btn" id="resetCropBtn">איפוס בחירה</button>
        <button class="refine-btn" id="skipCropBtn">דלג — תמונה מלאה</button>
        <button class="go-btn" id="confirmCropBtn">אשר וסרוק את האזור</button>
      </div>
    </div>
    <div class="preview-row" id="previewRow" style="display:none;">
      <div class="preview-thumb">
        <img id="previewImg" alt="תצוגה מקדימה">
        <div class="scanbar" id="scanbar"></div>
      </div>
      <div class="preview-meta">
        <div class="fname" id="fname"></div>
        <div class="fhint" id="fhint">READY — הקישו לסריקה</div>
      </div>
      <button class="go-btn" id="goBtn">סרוק ומצא לקנייה</button>
    </div>
  </div>
  <div class="caption-note">// הזיהוי וההתאמות מתבססים על חיפוש ברשת בזמן אמת. סימוני מקורי/חיקוי ואמין/חשוד הם הערכה בלבד — בדקו כל מוכר בעצמכם לפני רכישה.</div>

  <div id="resultsArea"></div>

  <footer>SCANLINE — כלי עזר לזיהוי חפצים ואיתור נקודות מכירה · build v7</footer>
</div>

<script>
const dropZone = document.getElementById('dropZone');
const fileInput = document.getElementById('fileInput');
const cropStage = document.getElementById('cropStage');
const cropFrame = document.getElementById('cropFrame');
const cropImg = document.getElementById('cropImg');
const cropBox = document.getElementById('cropBox');
const resetCropBtn = document.getElementById('resetCropBtn');
const skipCropBtn = document.getElementById('skipCropBtn');
const confirmCropBtn = document.getElementById('confirmCropBtn');
const previewRow = document.getElementById('previewRow');
const previewImg = document.getElementById('previewImg');
const fname = document.getElementById('fname');
const fhint = document.getElementById('fhint');
const scanbar = document.getElementById('scanbar');
const goBtn = document.getElementById('goBtn');
const resultsArea = document.getElementById('resultsArea');

let currentBase64 = null;
let currentMediaType = null;
let currentDataUrl = null;
let currentListings = [];
let activeTypeFilter = 'all';
let activeTrustFilter = 'all';
let searchIsrael = false;

const israelToggle = document.getElementById('israelToggle');
israelToggle.addEventListener('click', () => {
  searchIsrael = !searchIsrael;
  israelToggle.classList.toggle('active', searchIsrael);
});

// Drag & drop is an enhancement on top of the native label-for click/tap,
// which is what actually opens the camera/gallery picker on mobile.
dropZone.addEventListener('dragover', e => { e.preventDefault(); dropZone.classList.add('dragover'); });
dropZone.addEventListener('dragleave', () => dropZone.classList.remove('dragover'));
dropZone.addEventListener('drop', e => {
  e.preventDefault(); dropZone.classList.remove('dragover');
  if(e.dataTransfer.files && e.dataTransfer.files[0]){
    handleFile(e.dataTransfer.files[0]);
  }
});
fileInput.addEventListener('change', e => {
  console.log('SCANLINE: file input change, files:', e.target.files && e.target.files.length);
  if(e.target.files && e.target.files[0]) handleFile(e.target.files[0]);
});

let pendingRawDataUrl = null;
let pendingRawMediaType = null;
let pendingFileName = null;
let cropBoxPixels = null;
let cropDragging = false;
let cropStartX = 0, cropStartY = 0;

function handleFile(file){
  if(!file.type.startsWith('image/')){ alert('אנא בחרו קובץ תמונה'); return; }
  const reader = new FileReader();
  reader.onload = () => {
    pendingRawDataUrl = reader.result;
    pendingRawMediaType = file.type;
    pendingFileName = file.name;
    cropBoxPixels = null;
    cropBox.style.display = 'none';
    cropImg.src = pendingRawDataUrl;
    cropStage.style.display = 'block';
    previewRow.style.display = 'none';
    resultsArea.innerHTML = '';
  };
  reader.onerror = () => alert('קריאת הקובץ נכשלה, נסו שוב');
  reader.readAsDataURL(file);
}

function updateCropBox(x,y,w,h){
  cropBox.style.left = x+'px';
  cropBox.style.top = y+'px';
  cropBox.style.width = w+'px';
  cropBox.style.height = h+'px';
  cropBoxPixels = {x,y,w,h};
}

cropFrame.addEventListener('pointerdown', e => {
  const rect = cropFrame.getBoundingClientRect();
  cropStartX = Math.max(0, Math.min(e.clientX - rect.left, rect.width));
  cropStartY = Math.max(0, Math.min(e.clientY - rect.top, rect.height));
  cropDragging = true;
  cropBox.style.display = 'block';
  updateCropBox(cropStartX, cropStartY, 0, 0);
  try{ cropFrame.setPointerCapture(e.pointerId); }catch(err){}
});
cropFrame.addEventListener('pointermove', e => {
  if(!cropDragging) return;
  const rect = cropFrame.getBoundingClientRect();
  const curX = Math.max(0, Math.min(e.clientX - rect.left, rect.width));
  const curY = Math.max(0, Math.min(e.clientY - rect.top, rect.height));
  const x = Math.min(cropStartX, curX);
  const y = Math.min(cropStartY, curY);
  const w = Math.abs(curX - cropStartX);
  const h = Math.abs(curY - cropStartY);
  updateCropBox(x, y, w, h);
});
cropFrame.addEventListener('pointerup', () => { cropDragging = false; });
cropFrame.addEventListener('pointercancel', () => { cropDragging = false; });

resetCropBtn.addEventListener('click', () => {
  cropBoxPixels = null;
  cropBox.style.display = 'none';
});

skipCropBtn.addEventListener('click', () => {
  finalizeImage(pendingRawDataUrl, pendingRawMediaType, pendingFileName);
});

confirmCropBtn.addEventListener('click', () => {
  const MIN_PX = 12;
  if(!cropBoxPixels || cropBoxPixels.w < MIN_PX || cropBoxPixels.h < MIN_PX){
    // No meaningful selection drawn — fall back to the full image.
    finalizeImage(pendingRawDataUrl, pendingRawMediaType, pendingFileName);
    return;
  }
  const rect = cropFrame.getBoundingClientRect();
  const scaleX = cropImg.naturalWidth / rect.width;
  const scaleY = cropImg.naturalHeight / rect.height;
  const sx = Math.round(cropBoxPixels.x * scaleX);
  const sy = Math.round(cropBoxPixels.y * scaleY);
  const sw = Math.round(cropBoxPixels.w * scaleX);
  const sh = Math.round(cropBoxPixels.h * scaleY);

  const canvas = document.createElement('canvas');
  canvas.width = sw;
  canvas.height = sh;
  const ctx = canvas.getContext('2d');
  ctx.drawImage(cropImg, sx, sy, sw, sh, 0, 0, sw, sh);
  const croppedDataUrl = canvas.toDataURL('image/jpeg', 0.92);
  finalizeImage(croppedDataUrl, 'image/jpeg', pendingFileName, true);
});

function finalizeImage(dataUrl, mediaType, fileName, wasCropped){
  currentDataUrl = dataUrl;
  currentMediaType = mediaType;
  currentBase64 = dataUrl.split(',')[1];
  previewImg.src = currentDataUrl;
  fname.textContent = fileName + (wasCropped ? ' (חתוך ומחודד)' : '');
  fhint.textContent = 'READY — הקישו לסריקה';
  cropStage.style.display = 'none';
  previewRow.style.display = 'flex';
  resultsArea.innerHTML = '';
}

goBtn.addEventListener('click', identifyObject);

async function identifyObject(){
  if(!currentBase64) return;
  goBtn.disabled = true;
  goBtn.textContent = 'סורק…';
  scanbar.classList.add('active');
  fhint.textContent = 'SCANNING…';
  resultsArea.innerHTML = `
    <div class="status-line"><div class="spinner"></div> מזהה את החפץ ומחפש נקודות מכירה ברשת…</div>
  `;

  const israelClause = searchIsrael
    ? `\nהמשתמש ביקש להעדיף תוצאות מישראל: תן עדיפות במיוחד לחנויות ישראליות (כמו KSP, איווארי, זאפ, יד2, שופרסל, TerminalX, סטארלינג ועוד), או לחנויות בינלאומיות שמאשרות משלוח לישראל בבירור. אם יש גם וגם, הצג את שתי האפשרויות אך סמן את הישראליות בבירור בשדה country.`
    : '';

  const systemPrompt = `אתה עוזר לזיהוי חפצים ואיתור מקורות קנייה.
בהינתן תמונה של חפץ, זהה מה זה:
- אם יש מותג/לוגו/דגם ברור — ציין אותם בשם המדויק.
- אם אין שום מותג או סימן מזהה (חפץ גנרי, יד-שנייה, מוצר ללא מותג) — אל תוותר ואל תחזיר "לא מזוהה". תאר אותו לפי מה שכן ניתן לראות: קטגוריה, חומר, צבע, צורה, סגנון, שימוש אפשרי (למשל "כוס קרמיקה כחולה בסגנון יפני, בערך 300 מ״ל"), והשתמש בתיאור הזה כדי לחפש מוצרים דומים/זהים במרקטפלייסים כמו AliExpress, Amazon, Etsy, eBay, Wish, וכן חנויות מקומיות רלוונטיות. במקרה כזה ציין את זה בתיאור ("זיהוי לפי מראה כללי, ללא מותג מזוהה") כדי שהמשתמש ידע שזו התאמה ויזואלית ולא זיהוי מדויק.
לאחר מכן השתמש בחיפוש ברשת כדי למצוא 5-8 מקומות אמיתיים לקנייה (חנויות רשמיות, מרקטפלייסים, קמעונאים).${israelClause}
עבור כל תוצאה, העריך:
- type: "מקורי" אם מדובר במוכר/פלטפורמה רשמיים או ידועים כאמינים למוצר מקורי, "חיקוי" אם יש סימנים לחיקוי/רפליקה (מחיר נמוך באופן חריג, ניסוח כמו "AAA quality", "inspired by" וכו), או "לא ידוע" אם אי אפשר לקבוע. עבור חפץ גנרי ללא מותג, type יהיה בדרך כלל "לא ידוע" אלא אם ברור שמדובר בהעתק של מוצר ממותג.
- trust: "אמין" למוכר/פלטפורמה מוכרים ובעלי מוניטין, "חשוד" אם יש סימני אזהרה (חוסר פרטי קשר, ביקורות גרועות, מחיר לא הגיוני), או "לא ידוע".
- country: מדינת המקור של המוכר/החנות (למשל "ישראל", "ארה״ב", "סין", "גרמניה") — קבע לפי הדומיין, השפה, כתובת החנות או פרטי המשלוח. אם לא ניתן לקבוע, כתוב "לא ידוע".
- city: עיר המוכר אם ידועה בבירור (למשל מכתובת עסק רשמית), אחרת null.
בנוסף, על סמך התוצאות שמצאת, תן הערכת שווי כללית למוצר עצמו (טווח מחירים סביר בשוק, לא מחיר של מוכר ספציפי) — למשל "כ-150-220 ₪" או "$40-60". אם אין מספיק מידע לאמוד שווי, כתוב null.
החזר אך ורק JSON תקני (ללא markdown, ללא טקסט נוסף, ללא סימוני קוד), במבנה הבא:
{
  "item_name": "שם החפץ בעברית",
  "description": "תיאור קצר בן 1-2 משפטים בעברית",
  "estimated_value": "טווח שווי משוער של המוצר, או null",
  "listings": [
    {
      "seller": "שם החנות/האתר",
      "url": "קישור ישיר לעמוד המוצר או לחנות",
      "price": "מחיר משוער אם ידוע, אחרת null",
      "type": "מקורי" | "חיקוי" | "לא ידוע",
      "trust": "אמין" | "חשוד" | "לא ידוע",
      "country": "מדינת המוכר או לא ידוע",
      "city": "עיר המוכר או null",
      "note": "משפט קצר שמסביר את ההערכה"
    }
  ]
}
ודא שה-JSON תקין וניתן ל-parse.`;

  try{
    console.log('SCANLINE: sending identify request…');

    const fetchPromise = fetch("https://api.anthropic.com/v1/messages", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({
        model: "claude-sonnet-4-6",
        max_tokens: 8000,
        system: systemPrompt,
        messages: [
          {
            role: "user",
            content: [
              { type: "image", source: { type: "base64", media_type: currentMediaType, data: currentBase64 } },
              { type: "text", text: "זהה את החפץ בתמונה ומצא איפה אפשר לקנות אותו. החזר רק JSON לפי המבנה שהוגדר." }
            ]
          }
        ],
        tools: [ Object.assign(
          { type: "web_search_20250305", name: "web_search", max_uses: 7 },
          searchIsrael ? { user_location: { type: "approximate", country: "IL", timezone: "Asia/Jerusalem" } } : {}
        ) ]
      })
    });

    const timeoutPromise = new Promise((_, reject) => {
      setTimeout(() => reject(new Error('__SCANLINE_TIMEOUT__')), 55000);
    });

    const response = await Promise.race([fetchPromise, timeoutPromise]);

    console.log('SCANLINE: response status', response.status);

    if(!response.ok){
      let bodyText = '';
      try{ bodyText = await response.text(); }catch(e){}
      console.log('SCANLINE: error body', bodyText);
      throw new Error("שגיאת שרת (" + response.status + ")" + (bodyText ? ": " + bodyText.slice(0,200) : ""));
    }

    const data = await response.json();
    console.log('SCANLINE: raw response', JSON.stringify(data).slice(0, 2000));

    const textParts = (data.content || []).filter(b => b.type === "text").map(b => b.text);
    let raw = textParts.join("\n").trim();
    raw = raw.replace(/^```json\s*/i, '').replace(/^```\s*/,'').replace(/```\s*$/,'').trim();

    const firstBrace = raw.indexOf('{');
    const lastBrace = raw.lastIndexOf('}');
    if(firstBrace === -1 || lastBrace === -1){
      console.log('SCANLINE: no JSON braces found in text:', raw.slice(0,500));
      throw new Error("לא התקבל JSON תקין מהתשובה");
    }
    raw = raw.slice(firstBrace, lastBrace+1);

    let parsed;
    try{
      parsed = JSON.parse(raw);
    }catch(parseErr){
      console.log('SCANLINE: JSON parse failed on:', raw.slice(0,800));
      throw new Error("פענוח התשובה נכשל — " + parseErr.message);
    }

    renderResults(parsed);
    fhint.textContent = 'MATCH FOUND';

  }catch(err){
    console.log('SCANLINE: caught error', err);
    const msg = (err.message === '__SCANLINE_TIMEOUT__') ? 'הבקשה נמשכה יותר מדי זמן (55 שניות). נסו שוב, או נסו תמונה קלה/ברורה יותר.' : (err.message || 'שגיאה לא ידועה');
    resultsArea.innerHTML = `<div class="error-box"><strong>הזיהוי נכשל.</strong><br>${escapeHtml(msg)}<br><span style="opacity:.7;font-size:11.5px;">פרטים נוספים ב-Console Messages למטה.</span></div>`;
    fhint.textContent = 'שגיאה — נסו שוב';
  }finally{
    goBtn.disabled = false;
    goBtn.textContent = 'סרוק ומצא לקנייה';
    scanbar.classList.remove('active');
  }
}

function renderResults(parsed){
  currentListings = Array.isArray(parsed.listings) ? parsed.listings : [];
  activeTypeFilter = 'all';
  activeTrustFilter = 'all';

  const hasValue = parsed.estimated_value && parsed.estimated_value !== 'null';
  resultsArea.innerHTML = `
    <div class="item-head">
      <img src="${currentDataUrl}" alt="${escapeAttr(parsed.item_name||'')}">
      <div>
        <div class="eyebrow">זוהה</div>
        <h2>${escapeHtml(parsed.item_name || 'חפץ לא מזוהה')}</h2>
        <p>${escapeHtml(parsed.description || '')}</p>
        ${hasValue ? `<div class="value-pill">💰 שווי משוער: ${escapeHtml(parsed.estimated_value)}</div>` : ''}
      </div>
    </div>
    <div class="filters" id="filterBar"></div>
    <div class="listings" id="listingsBox"></div>
  `;
  renderFilters();
  renderListings();
}

function renderFilters(){
  const bar = document.getElementById('filterBar');
  bar.innerHTML = `
    <button class="chip ${activeTypeFilter==='all'?'active':''}" data-ftype="all">הכל</button>
    <button class="chip ${activeTypeFilter==='מקורי'?'active':''}" data-ftype="מקורי">מקורי בלבד</button>
    <button class="chip ${activeTypeFilter==='חיקוי'?'active':''}" data-ftype="חיקוי">חיקוי בלבד</button>
    <span class="filter-sep"></span>
    <button class="chip ${activeTrustFilter==='all'?'active':''}" data-ftrust="all">כל המוכרים</button>
    <button class="chip ${activeTrustFilter==='אמין'?'active':''}" data-ftrust="אמין">אמינים בלבד</button>
    <button class="chip ${activeTrustFilter==='חשוד'?'active':''}" data-ftrust="חשוד">להוציא חשודים</button>
  `;
  bar.querySelectorAll('[data-ftype]').forEach(btn=>{
    btn.addEventListener('click', ()=>{ activeTypeFilter = btn.dataset.ftype; renderFilters(); renderListings(); });
  });
  bar.querySelectorAll('[data-ftrust]').forEach(btn=>{
    btn.addEventListener('click', ()=>{ activeTrustFilter = btn.dataset.ftrust; renderFilters(); renderListings(); });
  });
}

function renderListings(){
  const box = document.getElementById('listingsBox');
  let filtered = currentListings.filter(l=>{
    if(activeTypeFilter !== 'all' && l.type !== activeTypeFilter) return false;
    if(activeTrustFilter === 'אמין' && l.trust !== 'אמין') return false;
    if(activeTrustFilter === 'חשוד' && l.trust === 'חשוד') return false;
    return true;
  });

  if(filtered.length === 0){
    box.innerHTML = `<div class="empty-state">// אין תוצאות שתואמות את הסינון הנוכחי</div>`;
    return;
  }

  box.innerHTML = filtered.map(l => {
    const typeClass = l.type === 'מקורי' ? 'orig' : (l.type === 'חיקוי' ? 'replica' : 'unknown-type');
    const trustClass = l.trust === 'אמין' ? 'trusted' : (l.trust === 'חשוד' ? 'suspect' : 'unknown-trust');
    let domain = '';
    try{ domain = l.url ? new URL(l.url).hostname.replace('www.','') : ''; }catch(e){ domain = l.url || ''; }
    const originParts = [l.city, l.country].filter(v => v && v !== 'null' && v !== 'לא ידוע');
    const originLabel = originParts.length ? originParts.join(' · ') : (l.country && l.country !== 'null' ? l.country : '');
    return `
      <div class="listing">
        <div class="l-top">
          <div class="l-seller">${escapeHtml(l.seller || 'מוכר לא ידוע')}</div>
          ${l.price ? `<div class="l-price">${escapeHtml(l.price)}</div>` : ''}
        </div>
        ${l.note ? `<div class="l-note">${escapeHtml(l.note)}</div>` : ''}
        <div class="l-tags">
          <span class="tag ${typeClass}">${escapeHtml(l.type || 'לא ידוע')}</span>
          <span class="tag ${trustClass}">${escapeHtml(l.trust || 'לא ידוע')}</span>
          ${originLabel ? `<span class="tag origin-tag">📍 ${escapeHtml(originLabel)}</span>` : ''}
        </div>
        ${l.url ? `
          <a class="buy-btn" href="${escapeAttr(l.url)}" target="_blank" rel="noopener noreferrer">
            <span>מעבר לרכישה</span><span class="arrow">←</span>
          </a>
          <div class="l-domain">${escapeHtml(domain)}</div>
        ` : ''}
      </div>
    `;
  }).join('');
}

function escapeHtml(str){
  return String(str).replace(/[&<>"']/g, m => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[m]));
}
function escapeAttr(str){ return escapeHtml(str); }
</script>
</body>
</html>
