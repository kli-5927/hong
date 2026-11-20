<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>캠핑족</title>
  <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>⛺</text></svg>" />
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/variable/pretendardvariable.min.css" />
  <script>
    // 화면에 오류를 보여주는 장치 (문제가 생기면 무엇이 잘못됐는지 바로 보이게)
    window.__showError = function (msg) {
      var box = document.getElementById("boot-error");
      if (!box) { box = document.createElement("pre"); box.id = "boot-error";
        box.style.cssText = "position:fixed;left:12px;right:12px;bottom:12px;z-index:9999;background:#fff3f3;color:#a00;border:1px solid #e6b3b3;border-radius:10px;padding:12px;font-size:13px;white-space:pre-wrap;max-height:40vh;overflow:auto";
        (document.body || document.documentElement).appendChild(box); }
      box.textContent = "⚠ 오류가 났어요. 이 내용을 복사해서 알려주세요.

" + msg;
    };
    window.addEventListener("error", function (e) { window.__showError((e.message || "스크립트를 불러오지 못했어요") + (e.filename ? "
" + e.filename + ":" + e.lineno : "") ); }, true);
    window.addEventListener("load", function () {
      var miss = [];
      if (!window.React) miss.push("React");
      if (!window.ReactDOM) miss.push("ReactDOM");
      if (!window.Babel) miss.push("Babel");
      if (!window.supabase) miss.push("Supabase");
      if (miss.length) window.__showError("외부 라이브러리를 불러오지 못했어요: " + miss.join(", ") + "
인터넷 연결이나 학교·회사 네트워크 차단을 확인해 주세요.");
    });
  </script>
  <script src="https://unpkg.com/react@18.3.1/umd/react.production.min.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@18.3.1/umd/react-dom.production.min.js" crossorigin></script>
  <script src="https://unpkg.com/@babel/standalone@7.26.10/babel.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2.45.4/dist/umd/supabase.js"></script>
  <style>
:root{
  --g900:#14291d; --g800:#1b3a28; --g700:#245035; --g600:#2f6b45; --g500:#3f8558; --g100:#e3ede5; --g50:#f1f5f0;
  --bg:#f3f1ea; --card:#fffdf8; --line:#ddd8ca; --text:#1f2a22; --muted:#6b7468;
  --warn:#c27a12; --warn-bg:#fdf3e1; --danger:#b23a3a;
}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--text);
  font-family:"Pretendard Variable",Pretendard,-apple-system,BlinkMacSystemFont,"Apple SD Gothic Neo","Malgun Gothic",sans-serif;
  font-size:15px;line-height:1.55;-webkit-font-smoothing:antialiased}
h1,h2,h3{margin:0;letter-spacing:-.02em}
h2{font-size:1.2rem;margin-bottom:.6rem} h3{font-size:1.05rem}
input,textarea,select{font:inherit;color:inherit;border:1px solid var(--line);border-radius:10px;padding:.55rem .7rem;background:#fff;width:100%;min-width:0}
input:focus,textarea:focus,select:focus{outline:2px solid var(--g500);outline-offset:-1px;border-color:transparent}
textarea{resize:vertical}
select{width:auto}
button{font:inherit;cursor:pointer}
.btn{border:1px solid var(--line);background:#fff;color:var(--text);border-radius:10px;padding:.5rem .9rem;font-weight:600;white-space:nowrap}
.btn:hover:not(:disabled){border-color:var(--g500)}
.btn:disabled{opacity:.4;cursor:default}
.btn.primary{background:var(--g700);border-color:var(--g700);color:#fff}
.btn.primary:hover:not(:disabled){background:var(--g800)}
.btn.ghost{background:transparent;border-color:transparent}
.btn.ghost:hover:not(:disabled){background:var(--g50);border-color:var(--line)}
.btn.danger{background:var(--danger);border-color:var(--danger);color:#fff}
.btn.danger-ghost{background:transparent;color:var(--danger);border-color:#e9c9c9}
.btn.sm{padding:.25rem .55rem;font-size:.85rem;border-radius:8px}
.btn.full{width:100%;padding:.7rem}
.muted{color:var(--muted)} .small{font-size:.85rem}
.error{color:var(--danger);font-size:.9rem}
.row{display:flex;gap:.5rem;align-items:center}
.row.between{justify-content:space-between} .row.end{justify-content:flex-end} .row.wrap{flex-wrap:wrap}
.grow{flex:1}
.stack{display:flex;flex-direction:column;gap:1rem}
.stack-sm{display:flex;flex-direction:column;gap:.6rem;margin-top:.8rem}
.nowrap{white-space:nowrap}
.dot{display:inline-block;width:10px;height:10px;border-radius:50%;flex:none}
.dot.lg{width:14px;height:14px}
.card{background:var(--card);border:1px solid var(--line);border-radius:16px;padding:1.1rem 1.2rem}

/* 로그인 */
.center-screen{min-height:100vh;display:grid;place-items:center;padding:1rem}
.hero{background:radial-gradient(1200px 600px at 50% -10%,var(--g600),var(--g900))}
.narrow{width:100%;max-width:380px}
.login{text-align:center;display:flex;flex-direction:column;gap:.8rem;padding:2rem 1.5rem}
.login h1{font-size:1.8rem;color:var(--g800)}
.login-logo{font-size:2.6rem}
.name-grid{display:grid;grid-template-columns:1fr 1fr;gap:.6rem}
.name-btn{display:flex;align-items:center;justify-content:center;gap:.5rem;padding:.9rem;border:1px solid var(--line);border-radius:12px;background:#fff;font-weight:700;font-size:1.05rem}
.name-btn:hover{border-color:var(--g500);background:var(--g50)}

/* 상단 */
.top{background:var(--g800);color:#fff;position:sticky;top:0;z-index:10;box-shadow:0 2px 10px rgba(0,0,0,.15)}
.top-inner{max-width:1080px;margin:0 auto;padding:.8rem 1rem .4rem;display:flex;justify-content:space-between;align-items:center;gap:1rem;flex-wrap:wrap}
.brand{display:flex;align-items:center;gap:.6rem}
.brand h1{font-size:1.35rem}
.logo{font-size:1.8rem}
.sub{font-size:.8rem;color:#b9d0bf}
.who{display:flex;align-items:center;gap:.4rem;font-size:.95rem}
.who .btn.ghost{color:#d6e6da}
.who .btn.ghost:hover{background:rgba(255,255,255,.1);border-color:transparent}
.tabs{max-width:1080px;margin:0 auto;display:flex;gap:.2rem;padding:0 .6rem;overflow-x:auto;scrollbar-width:none}
.tab{background:none;border:none;color:#b9d0bf;padding:.6rem .8rem;font-weight:600;border-bottom:3px solid transparent;white-space:nowrap}
.tab.on{color:#fff;border-bottom-color:#9fd3ad}
.tab:hover{color:#fff}
.demo-bar{background:var(--warn-bg);color:#7a4d0c;text-align:center;padding:.45rem 1rem;font-size:.85rem;border-bottom:1px solid #f0ddb6}
.demo-bar.err{background:#fbe9e9;color:var(--danger)}
.main{max-width:1080px;margin:0 auto;padding:1.2rem 1rem 4rem}

/* 통계 */
.stats{display:grid;grid-template-columns:repeat(auto-fill,minmax(160px,1fr));gap:.7rem}
.stat{background:var(--card);border:1px solid var(--line);border-radius:14px;padding:.8rem 1rem}
.stat.mine{border-color:var(--g500);box-shadow:0 0 0 1px var(--g500) inset}
.stat-name{display:flex;align-items:center;gap:.4rem;font-weight:700}
.stat-main{font-size:.95rem;margin-top:.2rem}
.stat-main b{font-size:1.6rem;color:var(--g700);margin-right:.1rem}
.stat-sub{font-size:.82rem;color:var(--muted)}
.warn{color:var(--warn);font-weight:600}

/* 달력 */
.cal-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:.6rem}
.cal-head h2{margin:0}
.cal{display:grid;grid-template-columns:repeat(7,minmax(0,1fr));gap:4px}
.cal-dow{text-align:center;font-size:.8rem;font-weight:700;color:var(--muted);padding:.2rem 0}
.sun{color:#c0392b!important} .sat{color:#2c6aa0!important}
.cal-cell{min-height:86px;border:1px solid var(--line);border-radius:10px;background:#fff;padding:.3rem;display:flex;flex-direction:column;align-items:stretch;text-align:left;gap:.2rem;transition:border-color .15s}
.cal-cell:hover:not(:disabled){border-color:var(--g500);background:var(--g50)}
.cal-cell.empty{border:none;background:none}
.cal-cell.out{background:#eeece5;border-color:transparent;cursor:default}
.cal-cell.out .cal-num{color:#b9b5aa!important}
.cal-cell.past{background:#f6f5f0}
.cal-cell.past .chip{opacity:.65}
.cal-cell.today{box-shadow:0 0 0 2px var(--g600) inset}
.cal-cell.conflict{border-color:var(--warn);background:var(--warn-bg)}
.cal-num{font-weight:700;font-size:.85rem}
.cal-chips{display:flex;flex-direction:column;gap:2px}
.chip{display:block;font-size:.74rem;font-weight:700;color:#fff;border-radius:6px;padding:1px 5px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap;border:1px solid transparent}
.chip.later{background:#fff;font-weight:600}
.chip i{font-style:normal;opacity:.85;margin-right:3px;font-size:.68rem}
.legend{margin:.8rem 0 0}

/* 목록 */
.list{list-style:none;margin:.6rem 0;padding:0;display:flex;flex-direction:column;gap:.4rem}
.list-item{display:flex;align-items:center;gap:.6rem;padding:.55rem .7rem;border:1px solid var(--line);border-radius:10px;background:#fff;flex-wrap:wrap}
.list-item.conflict{border-color:var(--warn);background:var(--warn-bg)}
.link{background:none;border:none;padding:0;font-weight:700;color:var(--g700);text-decoration:underline;text-underline-offset:3px}
.names{display:flex;gap:.6rem;flex:1;flex-wrap:wrap}
.names .first{font-weight:700}
.names .later-name{color:var(--muted)}
.badge{font-size:.75rem;padding:.1rem .45rem;border-radius:999px;background:var(--g100)}
.badge.warn{background:#f8e2b8;color:#7a4d0c}
.check{display:flex;align-items:center;gap:.4rem;cursor:pointer;font-size:.9rem}
.check input{width:auto}

/* 모달 */
.modal-bg{position:fixed;inset:0;background:rgba(10,25,15,.45);display:grid;place-items:center;padding:1rem;z-index:50}
.modal{background:var(--card);border-radius:16px;padding:1.2rem;width:100%;max-width:420px;max-height:90vh;overflow:auto;box-shadow:0 20px 50px rgba(0,0,0,.25)}
.rank-list{list-style:none;padding:0;margin:.8rem 0;display:flex;flex-direction:column;gap:.4rem}
.rank-list li{display:flex;align-items:center;gap:.5rem;padding:.5rem .6rem;background:#fff;border:1px solid var(--line);border-radius:10px}
.rank-list li:first-child{border-color:var(--g500);background:var(--g50)}
.rank{font-size:.78rem;font-weight:700;background:var(--g700);color:#fff;border-radius:6px;padding:.05rem .4rem}
.rank-list li:not(:first-child) .rank{background:#9aa39a}
.rank-list .small{margin-left:auto}
.note{background:var(--g50);border-radius:10px;padding:.55rem .7rem;font-size:.9rem}
.note.warn{background:var(--warn-bg);color:#7a4d0c;font-weight:600}

/* 게시판 */
.posts{list-style:none;padding:0;margin:1rem 0 0;display:flex;flex-direction:column;gap:.6rem}
.post{border:1px solid var(--line);border-radius:12px;padding:.7rem .9rem;background:#fff}
.post-head{display:flex;align-items:center;gap:.5rem;flex-wrap:wrap}
.post-actions{margin-left:auto}
.post-body{white-space:pre-wrap;margin-top:.3rem;word-break:break-word}
.doc{white-space:pre-wrap;background:#fff;border:1px solid var(--line);border-radius:12px;padding:1rem;line-height:1.75;word-break:break-word}

/* 체크리스트 */
.checklist{list-style:none;padding:0;margin:.6rem 0;display:flex;flex-direction:column;gap:.4rem}
.check.big{padding:.6rem .7rem;border:1px solid var(--line);border-radius:10px;background:#fff;font-size:.98rem}
.check.big input{width:18px;height:18px;accent-color:var(--g600)}
.check.big.done{color:var(--muted);text-decoration:line-through;background:var(--g50)}

/* 장비 */
.table-wrap{overflow-x:auto}
.tbl{width:100%;border-collapse:collapse;font-size:.92rem}
.tbl th{text-align:left;font-size:.8rem;color:var(--muted);font-weight:700;padding:.4rem .5rem;border-bottom:2px solid var(--line)}
.tbl td{padding:.5rem;border-bottom:1px solid var(--line);vertical-align:top}
.tbl tr.editing td{background:var(--g50)}
.equip-form{display:grid;grid-template-columns:2fr 1fr 1.5fr 2fr auto;gap:.5rem;margin-top:1rem}
.field{display:flex;flex-direction:column;font-size:.82rem;color:var(--muted);gap:.2rem}
.field input{width:auto}

.toast{position:fixed;left:50%;bottom:24px;transform:translateX(-50%);background:var(--g900);color:#fff;padding:.6rem 1.1rem;border-radius:999px;font-size:.9rem;z-index:60;box-shadow:0 6px 20px rgba(0,0,0,.25)}

@media (max-width:640px){
  body{font-size:14px}
  .main{padding:.8rem .6rem 4rem}
  .card{padding:.9rem;border-radius:14px}
  .cal{gap:2px}
  .cal-cell{min-height:64px;padding:.2rem;border-radius:7px}
  .chip{font-size:.66rem;padding:0 3px}
  .chip i{display:none}
  .who{font-size:.85rem}
  .equip-form{grid-template-columns:1fr 1fr}
  .equip-form .btn{grid-column:span 2}
  .stats{grid-template-columns:1fr 1fr}
}

  </style>
</head>
<body>
<div id="root"><p style="text-align:center;margin-top:40vh;color:#666">불러오는 중…</p></div>
<script type="text/babel" data-presets="react">
// =====================================================================
//  캠핑족 — 캠핑장 이용 예약 공유 사이트
//  아래 CONFIG만 바꾸면 됩니다.
//  SUPABASE_URL 이 비어 있으면 "체험 모드"로 동작해요
//  (이 브라우저에만 저장되고 다른 사람과 공유되지 않음).
// =====================================================================
const CONFIG = {
  SUPABASE_URL: "",        // 예: "https://xxxx.supabase.co"
  SUPABASE_ANON_KEY: "",   // Supabase > Project Settings > API > anon public key
  GROUP_PASSWORD: "camping", // 모임 공용 비밀번호
};

const { useState, useEffect, useMemo, useCallback } = React;
const DEMO = !CONFIG.SUPABASE_URL;
const sb = DEMO ? null : window.supabase.createClient(CONFIG.SUPABASE_URL, CONFIG.SUPABASE_ANON_KEY);

const TABLES = ["members", "reservations", "notices", "memos", "checklist", "equipment", "settings"];
const MEMBER_COLORS = ["#2f6b45", "#b5651d", "#3b6ea5", "#8e4b8e", "#a83b3b", "#6b7d1f", "#2a7f7f", "#7a5c2e"];
const DOW = ["일", "월", "화", "수", "목", "금", "토"];

const DEFAULT_CHECKLIST = [
  "쓰레기 분리수거하고 지정 장소에 버리기",
  "화로·숯불 완전히 끄기",
  "공용 장비 제자리에 정리",
  "전기·조명 끄기",
  "사이트 바닥 정리",
  "사용 후 메모 남기기",
];
const DEFAULT_INFO = `■ 캠핑장 이름:
■ 주소:
■ 관리사무소 연락처:
■ 출입 방법:
■ 체크인 / 체크아웃 시간:
■ 이용 수칙:
■ 쓰레기 처리:
■ 주변 마트·편의점:`;

// ---------- 작은 도구들 ----------
const uid = () => (window.crypto && crypto.randomUUID ? crypto.randomUUID() : String(Date.now()) + Math.random().toString(16).slice(2));
const pad = (n) => String(n).padStart(2, "0");
const ymd = (d) => `${d.getFullYear()}-${pad(d.getMonth() + 1)}-${pad(d.getDate())}`;
const parseDate = (s) => { const [y, m, d] = s.split("-").map(Number); return new Date(y, m - 1, d); };
const addDays = (s, n) => { const d = parseDate(s); d.setDate(d.getDate() + n); return ymd(d); };
const fmtNight = (s) => { const d = parseDate(s); return `${d.getMonth() + 1}월 ${d.getDate()}일(${DOW[d.getDay()]})`; };
const fmtShort = (s) => { const d = parseDate(s); return `${d.getMonth() + 1}/${d.getDate()}`; };
const fmtTime = (iso) => { if (!iso) return ""; const d = new Date(iso); return `${d.getFullYear()}.${d.getMonth() + 1}.${d.getDate()} ${pad(d.getHours())}:${pad(d.getMinutes())}`; };
const lsGet = (k) => { try { return localStorage.getItem(k); } catch (e) { return null; } };
const lsSet = (k, v) => { try { v == null ? localStorage.removeItem(k) : localStorage.setItem(k, v); } catch (e) {} };
const byCreated = (a, b) => (a.created_at < b.created_at ? -1 : a.created_at > b.created_at ? 1 : String(a.id) < String(b.id) ? -1 : 1);
const bySort = (a, b) => (a.sort ?? 0) - (b.sort ?? 0) || byCreated(a, b);

// ---------- 데이터 (Supabase 또는 체험 모드) ----------
const DEMO_KEY = "campjok_demo_v1";
function demoSeed() {
  const now = new Date().toISOString();
  return {
    members: ["회원1", "회원2", "회원3", "회원4"].map((name, i) => ({ id: uid(), name, sort: i, created_at: now })),
    reservations: [], notices: [], memos: [], equipment: [],
    checklist: DEFAULT_CHECKLIST.map((text, i) => ({ id: uid(), text, sort: i, created_at: now })),
    settings: [
      { key: "period_start", value: "2026-12-01" },
      { key: "period_end", value: "2027-02-28" },
      { key: "info", value: DEFAULT_INFO },
    ],
  };
}
function demoLoad() {
  try { const d = JSON.parse(lsGet(DEMO_KEY)); if (d && d.members) return d; } catch (e) {}
  const d = demoSeed(); demoSave(d); return d;
}
function demoSave(d) { lsSet(DEMO_KEY, JSON.stringify(d)); }

const api = {
  async loadAll() {
    if (DEMO) return demoLoad();
    const out = {};
    await Promise.all(TABLES.map(async (t) => {
      const { data, error } = await sb.from(t).select("*");
      if (error) throw error;
      out[t] = data || [];
    }));
    return out;
  },
  async insert(t, rows) {
    const list = Array.isArray(rows) ? rows : [rows];
    if (!list.length) return;
    if (DEMO) {
      const d = demoLoad();
      list.forEach((row, i) => {
        if (t === "reservations" && d.reservations.some((r) => r.member_id === row.member_id && r.night === row.night)) return;
        d[t].push({ id: uid(), created_at: new Date(Date.now() + i).toISOString(), ...row });
      });
      demoSave(d); return;
    }
    const { error } = await sb.from(t).insert(list);
    if (error && error.code !== "23505") throw error; // 23505: 이미 신청한 날짜
  },
  async update(t, id, patch) {
    if (DEMO) { const d = demoLoad(); d[t] = d[t].map((r) => (r.id === id ? { ...r, ...patch } : r)); demoSave(d); return; }
    const { error } = await sb.from(t).update(patch).eq("id", id);
    if (error) throw error;
  },
  async remove(t, id) {
    if (DEMO) {
      const d = demoLoad(); d[t] = d[t].filter((r) => r.id !== id);
      if (t === "members") d.reservations = d.reservations.filter((r) => r.member_id !== id);
      demoSave(d); return;
    }
    const { error } = await sb.from(t).delete().eq("id", id);
    if (error) throw error;
  },
  async setSetting(key, value, by) {
    const row = { key, value, updated_by: by, updated_at: new Date().toISOString() };
    if (DEMO) { const d = demoLoad(); d.settings = d.settings.filter((s) => s.key !== key).concat(row); demoSave(d); return; }
    const { error } = await sb.from("settings").upsert(row);
    if (error) throw error;
  },
};

// =====================================================================
//  화면
// =====================================================================
function App() {
  const [authed, setAuthed] = useState(() => lsGet("campjok_auth") === "1");
  const [meId, setMeId] = useState(() => lsGet("campjok_member"));
  const [data, setData] = useState(null);
  const [loadErr, setLoadErr] = useState("");
  const [tab, setTab] = useState("calendar");
  const [toast, setToast] = useState("");

  const refresh = useCallback(async () => {
    try { setData(await api.loadAll()); setLoadErr(""); }
    catch (e) { setLoadErr("데이터를 불러오지 못했어요: " + (e.message || e)); }
  }, []);

  useEffect(() => {
    if (!authed) return;
    refresh();
    const timer = setInterval(refresh, 20000);
    window.addEventListener("focus", refresh);
    return () => { clearInterval(timer); window.removeEventListener("focus", refresh); };
  }, [authed, refresh]);

  const showToast = (m) => { setToast(m); setTimeout(() => setToast(""), 2200); };
  const run = async (fn, msg) => {
    try { await fn(); await refresh(); if (msg) showToast(msg); }
    catch (e) { showToast("오류: " + (e.message || e)); }
  };

  if (!authed) return <PasswordGate onOk={() => { lsSet("campjok_auth", "1"); setAuthed(true); }} />;
  if (!data) return <div className="center-screen"><div className="card narrow">{loadErr || "불러오는 중…"}</div></div>;

  const members = [...data.members].sort(bySort);
  const colorOf = Object.fromEntries(members.map((m, i) => [m.id, MEMBER_COLORS[i % MEMBER_COLORS.length]]));
  const me = members.find((m) => m.id === meId);
  const settings = Object.fromEntries(data.settings.map((s) => [s.key, s]));

  if (!me) {
    return <PickName members={members} colorOf={colorOf}
      onPick={(id) => { lsSet("campjok_member", id); setMeId(id); }}
      onAdd={(name) => run(() => api.insert("members", { name, sort: members.length }), "이름을 추가했어요")} />;
  }

  const ctx = { data, members, me, colorOf, settings, run, showToast };
  const start = settings.period_start?.value || "2026-12-01";
  const end = settings.period_end?.value || "2027-02-28";

  const TABS = [
    ["calendar", "📅 예약 달력"], ["notices", "📢 공지"], ["info", "🏕️ 캠핑장 정보"],
    ["checklist", "✅ 체크리스트·메모"], ["equipment", "🎒 공용 장비"], ["settings", "⚙️ 설정"],
  ];

  return (
    <div className="app">
      <header className="top">
        <div className="top-inner">
          <div className="brand">
            <span className="logo">⛺</span>
            <div>
              <h1>캠핑족</h1>
              <div className="sub">이용 기간 {start.replaceAll("-", ".")} ~ {end.replaceAll("-", ".")}</div>
            </div>
          </div>
          <div className="who">
            <span className="dot" style={{ background: colorOf[me.id] }} />
            <b>{me.name}</b>님
            <button className="btn ghost sm" onClick={() => { lsSet("campjok_member", null); setMeId(null); }}>이름 변경</button>
            <button className="btn ghost sm" onClick={() => { lsSet("campjok_auth", null); setAuthed(false); }}>나가기</button>
          </div>
        </div>
        <nav className="tabs">
          {TABS.map(([k, label]) => (
            <button key={k} className={"tab" + (tab === k ? " on" : "")} onClick={() => setTab(k)}>{label}</button>
          ))}
        </nav>
      </header>

      {DEMO && <div className="demo-bar">체험 모드예요. 지금 입력한 내용은 이 브라우저에만 저장돼요. Supabase를 연결하면 모임원과 공유돼요.</div>}
      {loadErr && <div className="demo-bar err">{loadErr}</div>}

      <main className="main">
        {tab === "calendar" && <CalendarPage ctx={ctx} start={start} end={end} />}
        {tab === "notices" && <Board ctx={ctx} table="notices" title="공지" placeholder="모임원 모두에게 알릴 내용을 적어 주세요" />}
        {tab === "info" && <InfoPage ctx={ctx} />}
        {tab === "checklist" && <ChecklistPage ctx={ctx} />}
        {tab === "equipment" && <EquipmentPage ctx={ctx} />}
        {tab === "settings" && <SettingsPage ctx={ctx} start={start} end={end} />}
      </main>
      {toast && <div className="toast">{toast}</div>}
    </div>
  );
}

// ---------- 로그인 ----------
function PasswordGate({ onOk }) {
  const [pw, setPw] = useState("");
  const [bad, setBad] = useState(false);
  const submit = (e) => { e.preventDefault(); if (pw === CONFIG.GROUP_PASSWORD) onOk(); else setBad(true); };
  return (
    <div className="center-screen hero">
      <form className="card narrow login" onSubmit={submit}>
        <div className="login-logo">⛺</div>
        <h1>캠핑족</h1>
        <p className="muted">모임 공용 비밀번호를 입력해 주세요</p>
        <input type="password" value={pw} autoFocus placeholder="비밀번호"
          onChange={(e) => { setPw(e.target.value); setBad(false); }} />
        {bad && <div className="error">비밀번호가 맞지 않아요</div>}
        <button className="btn primary full">들어가기</button>
        {DEMO && <p className="muted small">체험 모드 비밀번호: {CONFIG.GROUP_PASSWORD}</p>}
      </form>
    </div>
  );
}

function PickName({ members, colorOf, onPick, onAdd }) {
  const [name, setName] = useState("");
  return (
    <div className="center-screen hero">
      <div className="card narrow login">
        <h2>누구신가요?</h2>
        <p className="muted">이름을 골라 주세요</p>
        <div className="name-grid">
          {members.map((m) => (
            <button key={m.id} className="name-btn" onClick={() => onPick(m.id)}>
              <span className="dot lg" style={{ background: colorOf[m.id] }} />{m.name}
            </button>
          ))}
        </div>
        <form className="row" onSubmit={(e) => { e.preventDefault(); if (name.trim()) { onAdd(name.trim()); setName(""); } }}>
          <input value={name} onChange={(e) => setName(e.target.value)} placeholder="목록에 없으면 이름 추가" />
          <button className="btn">추가</button>
        </form>
      </div>
    </div>
  );
}

// ---------- 예약 달력 ----------
function useNightMap(data) {
  return useMemo(() => {
    const map = {};
    [...data.reservations].sort(byCreated).forEach((r) => { (map[r.night] = map[r.night] || []).push(r); });
    return map;
  }, [data.reservations]);
}

function CalendarPage({ ctx, start, end }) {
  const { data, members, me, colorOf, run } = ctx;
  const nightMap = useNightMap(data);
  const today = ymd(new Date());
  const nameOf = Object.fromEntries(members.map((m) => [m.id, m.name]));

  // 기간 안의 달 목록
  const months = useMemo(() => {
    const list = []; const s = parseDate(start); const e = parseDate(end);
    const d = new Date(s.getFullYear(), s.getMonth(), 1);
    while (d <= e && list.length < 60) { list.push([d.getFullYear(), d.getMonth()]); d.setMonth(d.getMonth() + 1); }
    return list;
  }, [start, end]);
  const initialIdx = Math.max(0, months.findIndex(([y, m]) => y === new Date().getFullYear() && m === new Date().getMonth()));
  const [mi, setMi] = useState(initialIdx);
  const idx = Math.min(mi, months.length - 1);
  const [selected, setSelected] = useState(null);
  const [onlyMine, setOnlyMine] = useState(false);

  // 회원별 통계
  const stats = members.map((m) => {
    let used = 0, upcoming = 0, waiting = 0;
    Object.entries(nightMap).forEach(([night, list]) => {
      const rank = list.findIndex((r) => r.member_id === m.id);
      if (rank < 0) return;
      if (rank === 0) { night < today ? used++ : upcoming++; } else if (night >= today) waiting++;
    });
    return { m, used, upcoming, waiting };
  });

  if (!months.length) return <div className="card">설정에서 이용 기간을 확인해 주세요.</div>;
  const [year, month] = months[idx];
  const first = new Date(year, month, 1);
  const daysInMonth = new Date(year, month + 1, 0).getDate();
  const cells = [];
  for (let i = 0; i < first.getDay(); i++) cells.push(null);
  for (let d = 1; d <= daysInMonth; d++) cells.push(ymd(new Date(year, month, d)));
  while (cells.length % 7) cells.push(null);

  const upcomingNights = Object.keys(nightMap).filter((n) => n >= today).sort()
    .filter((n) => !onlyMine || nightMap[n].some((r) => r.member_id === me.id));

  return (
    <div className="stack">
      <section className="stats">
        {stats.map(({ m, used, upcoming, waiting }) => (
          <div key={m.id} className={"stat" + (m.id === me.id ? " mine" : "")}>
            <div className="stat-name"><span className="dot" style={{ background: colorOf[m.id] }} />{m.name}</div>
            <div className="stat-main"><b>{used}</b>박 사용</div>
            <div className="stat-sub">예정 {upcoming}박{waiting > 0 && <span className="warn"> · 조율 필요 {waiting}일</span>}</div>
          </div>
        ))}
      </section>

      <section className="card">
        <div className="cal-head">
          <button className="btn ghost" disabled={idx === 0} onClick={() => setMi(idx - 1)}>◀</button>
          <h2>{year}년 {month + 1}월</h2>
          <button className="btn ghost" disabled={idx === months.length - 1} onClick={() => setMi(idx + 1)}>▶</button>
        </div>
        <div className="cal">
          {DOW.map((d, i) => <div key={d} className={"cal-dow" + (i === 0 ? " sun" : i === 6 ? " sat" : "")}>{d}</div>)}
          {cells.map((night, i) => {
            if (!night) return <div key={"e" + i} className="cal-cell empty" />;
            const inPeriod = night >= start && night <= end;
            const list = nightMap[night] || [];
            const dow = parseDate(night).getDay();
            const cls = ["cal-cell", inPeriod ? "" : "out", night === today ? "today" : "", night < today ? "past" : "",
              list.length > 1 ? "conflict" : "", list.some((r) => r.member_id === me.id) ? "has-mine" : ""].join(" ");
            return (
              <button key={night} className={cls} disabled={!inPeriod} onClick={() => setSelected(night)}>
                <span className={"cal-num" + (dow === 0 ? " sun" : dow === 6 ? " sat" : "")}>{parseDate(night).getDate()}</span>
                <span className="cal-chips">
                  {list.map((r, rank) => (
                    <span key={r.id} className={"chip" + (rank > 0 ? " later" : "")}
                      style={rank === 0 ? { background: colorOf[r.member_id] } : { borderColor: colorOf[r.member_id], color: colorOf[r.member_id] }}>
                      {list.length > 1 && <i>{rank + 1}</i>}{nameOf[r.member_id] || "?"}
                    </span>
                  ))}
                </span>
              </button>
            );
          })}
        </div>
        <p className="muted small legend">
          날짜를 누르면 신청하거나 취소할 수 있어요. 날짜는 <b>그날 밤 1박</b> 기준이에요.
          한 날짜에 여러 명이 신청하면 먼저 신청한 순서대로 <b>①②③</b> 순위가 붙어요.
          서로 이야기해서 정하고, 양보하는 사람이 신청을 취소하면 다음 사람이 1순위가 돼요.
        </p>
      </section>

      <section className="card">
        <div className="row between">
          <h3>다가오는 예약</h3>
          <label className="check"><input type="checkbox" checked={onlyMine} onChange={(e) => setOnlyMine(e.target.checked)} /> 내 신청만</label>
        </div>
        {upcomingNights.length === 0 ? <p className="muted">아직 예약이 없어요.</p> : (
          <ul className="list">
            {upcomingNights.map((night) => {
              const list = nightMap[night];
              const mine = list.find((r) => r.member_id === me.id);
              return (
                <li key={night} className={"list-item" + (list.length > 1 ? " conflict" : "")}>
                  <button className="link" onClick={() => setSelected(night)}>{fmtNight(night)} 밤</button>
                  <span className="names">
                    {list.map((r, rank) => (
                      <span key={r.id} className={rank === 0 ? "first" : "later-name"}>
                        {list.length > 1 ? `${rank + 1}순위 ` : ""}{nameOf[r.member_id]}
                      </span>
                    ))}
                  </span>
                  {list.length > 1 && <span className="badge warn">조율 필요</span>}
                  {mine && <button className="btn sm danger-ghost" onClick={() => {
                    if (confirm(`${fmtNight(night)} 신청을 취소할까요?`)) run(() => api.remove("reservations", mine.id), "취소했어요");
                  }}>취소</button>}
                </li>
              );
            })}
          </ul>
        )}
      </section>

      {selected && <DayModal ctx={ctx} night={selected} nightMap={nightMap} start={start} end={end} onClose={() => setSelected(null)} />}
    </div>
  );
}

function DayModal({ ctx, night, nightMap, start, end, onClose }) {
  const { me, members, colorOf, run } = ctx;
  const [count, setCount] = useState(1);
  const list = nightMap[night] || [];
  const nameOf = Object.fromEntries(members.map((m) => [m.id, m.name]));
  const mine = list.find((r) => r.member_id === me.id);
  const myRank = list.findIndex((r) => r.member_id === me.id) + 1;

  const maxCount = Math.min(14, Math.round((parseDate(end) - parseDate(night)) / 86400000) + 1);
  const nights = Array.from({ length: count }, (_, i) => addDays(night, i))
    .filter((n) => n <= end && !(nightMap[n] || []).some((r) => r.member_id === me.id));
  const lastNight = addDays(night, count - 1);

  const apply = () => run(async () => {
    await api.insert("reservations", nights.map((n) => ({ member_id: me.id, night: n })));
    onClose();
  }, `${nights.length}박 신청했어요`);

  return (
    <div className="modal-bg" onClick={onClose}>
      <div className="modal" onClick={(e) => e.stopPropagation()}>
        <div className="row between">
          <h3>{fmtNight(night)} 밤</h3>
          <button className="btn ghost sm" onClick={onClose}>닫기</button>
        </div>
        <p className="muted small">{fmtNight(night)} 체크인 → {fmtNight(addDays(night, 1))} 체크아웃</p>

        {list.length === 0 ? <p className="muted">아직 신청한 사람이 없어요.</p> : (
          <ol className="rank-list">
            {list.map((r, i) => (
              <li key={r.id}>
                <span className="rank">{i + 1}순위</span>
                <span className="dot" style={{ background: colorOf[r.member_id] }} />
                <b>{nameOf[r.member_id] || "?"}</b>
                <span className="muted small">{fmtTime(r.created_at)} 신청</span>
              </li>
            ))}
          </ol>
        )}
        {list.length > 1 && <div className="note warn">신청이 겹쳤어요. 서로 이야기해서 정해 주세요.</div>}

        {mine ? (
          <div className="stack-sm">
            <div className="note">내 순위: <b>{myRank}순위</b></div>
            <button className="btn danger full" onClick={() => run(async () => { await api.remove("reservations", mine.id); onClose(); }, "신청을 취소했어요")}>
              이 날 신청 취소
            </button>
          </div>
        ) : (
          <div className="stack-sm">
            <label className="row">
              <span>연속으로</span>
              <select value={count} onChange={(e) => setCount(Number(e.target.value))}>
                {Array.from({ length: Math.max(1, maxCount) }, (_, i) => i + 1).map((n) => <option key={n} value={n}>{n}박</option>)}
              </select>
              {count > 1 && <span className="muted small">{fmtShort(night)} ~ {fmtShort(lastNight)} 밤</span>}
            </label>
            <button className="btn primary full" disabled={!nights.length} onClick={apply}>
              {count > 1 ? `${nights.length}박 신청하기` : "이 날 신청하기"}
            </button>
            {list.length > 0 && <p className="muted small">신청하면 {list.length + 1}순위가 돼요.</p>}
          </div>
        )}
      </div>
    </div>
  );
}

// ---------- 공지 / 메모 게시판 ----------
function Board({ ctx, table, title, placeholder }) {
  const { data, me, run } = ctx;
  const [text, setText] = useState("");
  const [editId, setEditId] = useState(null);
  const [editText, setEditText] = useState("");
  const items = [...data[table]].sort(byCreated).reverse();

  return (
    <section className="card">
      <h2>{title}</h2>
      <form className="stack-sm" onSubmit={(e) => {
        e.preventDefault(); if (!text.trim()) return;
        run(() => api.insert(table, { author: me.name, content: text.trim() }), "올렸어요"); setText("");
      }}>
        <textarea rows={3} value={text} onChange={(e) => setText(e.target.value)} placeholder={placeholder} />
        <div className="row end"><button className="btn primary">올리기</button></div>
      </form>
      {items.length === 0 ? <p className="muted">아직 글이 없어요.</p> : (
        <ul className="posts">
          {items.map((p) => (
            <li key={p.id} className="post">
              <div className="post-head">
                <b>{p.author}</b><span className="muted small">{fmtTime(p.created_at)}{p.edited_at ? " (수정됨)" : ""}</span>
                {p.author === me.name && editId !== p.id && (
                  <span className="post-actions">
                    <button className="btn ghost sm" onClick={() => { setEditId(p.id); setEditText(p.content); }}>수정</button>
                    <button className="btn ghost sm" onClick={() => { if (confirm("삭제할까요?")) run(() => api.remove(table, p.id), "삭제했어요"); }}>삭제</button>
                  </span>
                )}
              </div>
              {editId === p.id ? (
                <div className="stack-sm">
                  <textarea rows={3} value={editText} onChange={(e) => setEditText(e.target.value)} />
                  <div className="row end">
                    <button className="btn ghost" onClick={() => setEditId(null)}>취소</button>
                    <button className="btn primary" onClick={() => { run(() => api.update(table, p.id, { content: editText, edited_at: new Date().toISOString() }), "수정했어요"); setEditId(null); }}>저장</button>
                  </div>
                </div>
              ) : <div className="post-body">{p.content}</div>}
            </li>
          ))}
        </ul>
      )}
    </section>
  );
}

// ---------- 캠핑장 정보 ----------
function InfoPage({ ctx }) {
  const { settings, me, run } = ctx;
  const info = settings.info || { value: "" };
  const [editing, setEditing] = useState(false);
  const [text, setText] = useState(info.value);
  return (
    <section className="card">
      <div className="row between">
        <h2>캠핑장 정보</h2>
        {!editing && <button className="btn" onClick={() => { setText(info.value || ""); setEditing(true); }}>수정</button>}
      </div>
      {editing ? (
        <div className="stack-sm">
          <textarea rows={16} value={text} onChange={(e) => setText(e.target.value)} />
          <div className="row end">
            <button className="btn ghost" onClick={() => setEditing(false)}>취소</button>
            <button className="btn primary" onClick={() => { run(() => api.setSetting("info", text, me.name), "저장했어요"); setEditing(false); }}>저장</button>
          </div>
        </div>
      ) : (
        <>
          <div className="doc">{info.value || "아직 정보가 없어요. 수정 버튼을 눌러 적어 주세요."}</div>
          {info.updated_by && <p className="muted small">마지막 수정: {info.updated_by} · {fmtTime(info.updated_at)}</p>}
        </>
      )}
    </section>
  );
}

// ---------- 체크리스트 + 사용 후 메모 ----------
function ChecklistPage({ ctx }) {
  const { data, run } = ctx;
  const items = [...data.checklist].sort(bySort);
  const [checked, setChecked] = useState({});
  const [editMode, setEditMode] = useState(false);
  const [newText, setNewText] = useState("");
  const done = items.filter((it) => checked[it.id]).length;

  const move = (i, dir) => {
    const a = items[i], b = items[i + dir]; if (!b) return;
    run(async () => { await api.update("checklist", a.id, { sort: b.sort ?? i + dir }); await api.update("checklist", b.id, { sort: a.sort ?? i }); });
  };

  return (
    <div className="stack">
      <section className="card">
        <div className="row between">
          <h2>사용 후 체크리스트</h2>
          <button className="btn" onClick={() => setEditMode(!editMode)}>{editMode ? "편집 끝" : "항목 편집"}</button>
        </div>
        {!editMode && <p className="muted small">떠나기 전에 하나씩 확인해 보세요. ({done}/{items.length}) — 체크 표시는 내 화면에만 보여요.</p>}
        <ul className="checklist">
          {items.map((it, i) => (
            <li key={it.id}>
              {editMode ? (
                <div className="row">
                  <input defaultValue={it.text} onBlur={(e) => { const v = e.target.value.trim(); if (v && v !== it.text) run(() => api.update("checklist", it.id, { text: v }), "수정했어요"); }} />
                  <button className="btn ghost sm" disabled={i === 0} onClick={() => move(i, -1)}>▲</button>
                  <button className="btn ghost sm" disabled={i === items.length - 1} onClick={() => move(i, 1)}>▼</button>
                  <button className="btn ghost sm" onClick={() => { if (confirm("이 항목을 삭제할까요?")) run(() => api.remove("checklist", it.id), "삭제했어요"); }}>삭제</button>
                </div>
              ) : (
                <label className={"check big" + (checked[it.id] ? " done" : "")}>
                  <input type="checkbox" checked={!!checked[it.id]} onChange={(e) => setChecked({ ...checked, [it.id]: e.target.checked })} />
                  {it.text}
                </label>
              )}
            </li>
          ))}
        </ul>
        {editMode && (
          <form className="row" onSubmit={(e) => { e.preventDefault(); if (!newText.trim()) return;
            const maxSort = items.reduce((mx, it) => Math.max(mx, it.sort ?? 0), -1);
            run(() => api.insert("checklist", { text: newText.trim(), sort: maxSort + 1 }), "추가했어요"); setNewText(""); }}>
            <input value={newText} onChange={(e) => setNewText(e.target.value)} placeholder="새 항목" />
            <button className="btn primary">추가</button>
          </form>
        )}
        {!editMode && done > 0 && <div className="row end"><button className="btn ghost sm" onClick={() => setChecked({})}>체크 초기화</button></div>}
      </section>
      <Board ctx={ctx} table="memos" title="사용 후 메모" placeholder="다음 사람에게 남길 말 (예: 장작 거의 다 씀, 랜턴 배터리 교체 필요)" />
    </div>
  );
}

// ---------- 공용 장비 ----------
function EquipmentPage({ ctx }) {
  const { data, me, run } = ctx;
  const items = [...data.equipment].sort(byCreated);
  const empty = { name: "", qty: "", location: "", note: "" };
  const [form, setForm] = useState(empty);
  const [editId, setEditId] = useState(null);
  const [edit, setEdit] = useState(empty);
  const F = (obj, set, k, ph) => <input value={obj[k] ?? ""} placeholder={ph} onChange={(e) => set({ ...obj, [k]: e.target.value })} />;

  return (
    <section className="card">
      <h2>공용 장비</h2>
      <div className="table-wrap">
        <table className="tbl">
          <thead><tr><th>장비</th><th>수량</th><th>보관 위치</th><th>상태·메모</th><th></th></tr></thead>
          <tbody>
            {items.length === 0 && <tr><td colSpan={5} className="muted">아직 등록된 장비가 없어요.</td></tr>}
            {items.map((it) => editId === it.id ? (
              <tr key={it.id} className="editing">
                <td>{F(edit, setEdit, "name", "장비")}</td><td>{F(edit, setEdit, "qty", "수량")}</td>
                <td>{F(edit, setEdit, "location", "위치")}</td><td>{F(edit, setEdit, "note", "메모")}</td>
                <td className="nowrap">
                  <button className="btn primary sm" onClick={() => { run(() => api.update("equipment", it.id, { name: edit.name, qty: edit.qty, location: edit.location, note: edit.note, updated_by: me.name }), "저장했어요"); setEditId(null); }}>저장</button>
                  <button className="btn ghost sm" onClick={() => setEditId(null)}>취소</button>
                </td>
              </tr>
            ) : (
              <tr key={it.id}>
                <td><b>{it.name}</b></td><td>{it.qty}</td><td>{it.location}</td>
                <td>{it.note}{it.updated_by && <div className="muted small">수정: {it.updated_by}</div>}</td>
                <td className="nowrap">
                  <button className="btn ghost sm" onClick={() => { setEditId(it.id); setEdit({ ...empty, ...it }); }}>수정</button>
                  <button className="btn ghost sm" onClick={() => { if (confirm(`'${it.name}'을(를) 삭제할까요?`)) run(() => api.remove("equipment", it.id), "삭제했어요"); }}>삭제</button>
                </td>
              </tr>
            ))}
          </tbody>
        </table>
      </div>
      <form className="equip-form" onSubmit={(e) => { e.preventDefault(); if (!form.name.trim()) return;
        run(() => api.insert("equipment", { ...form, name: form.name.trim(), updated_by: me.name }), "추가했어요"); setForm(empty); }}>
        {F(form, setForm, "name", "장비 이름 (예: 타프)")}{F(form, setForm, "qty", "수량")}
        {F(form, setForm, "location", "보관 위치")}{F(form, setForm, "note", "상태·메모")}
        <button className="btn primary">추가</button>
      </form>
    </section>
  );
}

// ---------- 설정 ----------
function SettingsPage({ ctx, start, end }) {
  const { members, me, colorOf, run, showToast, data } = ctx;
  const [s, setS] = useState(start);
  const [e, setE] = useState(end);
  const [newName, setNewName] = useState("");

  const savePeriod = () => {
    if (!s || !e || s > e) { showToast("시작일이 종료일보다 늦을 수 없어요"); return; }
    const outside = data.reservations.filter((r) => r.night < s || r.night > e).length;
    if (outside && !confirm(`새 기간 밖에 있는 신청 ${outside}건은 달력에 보이지 않게 돼요(기록은 남아요). 계속할까요?`)) return;
    run(async () => { await api.setSetting("period_start", s, me.name); await api.setSetting("period_end", e, me.name); }, "이용 기간을 바꿨어요");
  };

  return (
    <div className="stack">
      <section className="card">
        <h2>이용 기간</h2>
        <p className="muted small">캠핑장 대여 기간을 늘리거나 줄일 수 있어요. 달력은 이 기간 안에서만 신청할 수 있어요.</p>
        <div className="row wrap">
          <label className="field">시작일<input type="date" value={s} onChange={(ev) => setS(ev.target.value)} /></label>
          <span>~</span>
          <label className="field">종료일<input type="date" value={e} onChange={(ev) => setE(ev.target.value)} /></label>
          <button className="btn primary" onClick={savePeriod}>저장</button>
        </div>
      </section>

      <section className="card">
        <h2>모임원</h2>
        <ul className="list">
          {members.map((m) => (
            <li key={m.id} className="list-item">
              <span className="dot" style={{ background: colorOf[m.id] }} />
              <input className="grow" defaultValue={m.name} onBlur={(ev) => {
                const v = ev.target.value.trim();
                if (v && v !== m.name) run(() => api.update("members", m.id, { name: v }), "이름을 바꿨어요");
              }} />
              {m.id !== me.id && (
                <button className="btn ghost sm" onClick={() => {
                  if (confirm(`'${m.name}'을(를) 모임원에서 삭제할까요? 이 사람의 예약 신청도 함께 지워져요.`)) run(() => api.remove("members", m.id), "삭제했어요");
                }}>삭제</button>
              )}
            </li>
          ))}
        </ul>
        <form className="row" onSubmit={(ev) => { ev.preventDefault(); if (!newName.trim()) return;
          const maxSort = members.reduce((mx, m) => Math.max(mx, m.sort ?? 0), -1);
          run(() => api.insert("members", { name: newName.trim(), sort: maxSort + 1 }), "모임원을 추가했어요"); setNewName(""); }}>
          <input value={newName} onChange={(ev) => setNewName(ev.target.value)} placeholder="새 모임원 이름" />
          <button className="btn primary">추가</button>
        </form>
        <p className="muted small">이름 칸을 고친 뒤 다른 곳을 누르면 저장돼요.</p>
      </section>

      {DEMO && (
        <section className="card">
          <h2>체험 모드</h2>
          <p className="muted small">체험용 데이터를 처음 상태로 되돌려요.</p>
          <button className="btn danger" onClick={() => { if (confirm("체험 데이터를 모두 지울까요?")) { lsSet(DEMO_KEY, null); location.reload(); } }}>체험 데이터 초기화</button>
        </section>
      )}
    </div>
  );
}

ReactDOM.createRoot(document.getElementById("root")).render(<App />);

</script>
</body>
</html>
