/*
AyoFemi10 — Portfolio + Animated Neon Banner (single-file React component)

How to use
1. Copy this file into a React project (e.g. create-react-app, Vite + React).
2. Save as `src/App.jsx` and ensure Tailwind CSS is available (optional). The component uses Tailwind classes for quick styling; if you don't have Tailwind, the inline CSS in this file will still provide styling.
3. Run the project: `npm install` then `npm run dev` or `npm start`.

What's included
- Animated neon SVG banner (responsive)
- Flashy project cards for AYOMIKUN MD / PAIR / TG (placeholder links)
- GitHub stats widgets (image embeds)
- Contact section with email
- Download README button that generates the flashy README.md content as a file

Customize
- Replace `REPO_LINK_MD`, `REPO_LINK_PAIR`, `REPO_LINK_TG` with your repo URLs
- Replace email if needed
- Tweak colors, fonts, and images as you like
*/

import React from 'react';

const REPO_LINK_MD = 'https://github.com/AyoFemi10/AYOMIKUN-MD';
const REPO_LINK_PAIR = 'https://github.com/AyoFemi10/AYOMIKUN-PAIR';
const REPO_LINK_TG = 'https://github.com/AyoFemi10/AYOMIKUN-TG';
const EMAIL = 'emmanuelkelebe@gmail.com';

// Simple helper to download README content generated below
function downloadReadme() {
  const content = README_CONTENT;
  const blob = new Blob([content], { type: 'text/markdown' });
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url;
  a.download = 'README.md';
  a.click();
  URL.revokeObjectURL(url);
}

// The flashy README content (kept concise so file is manageable)
const README_CONTENT = `<!-- ULTRA FLASHY + ADVANCED PROFILE FOR AyoFemi10 -->

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Exo+2&size=36&duration=3000&pause=700&color=00F7FF&center=true&vCenter=true&width=1000&lines=Hey+I'm+Ayo+Femi+(AyoFemi10)!;Developer+%7C+Bot+Creator+%7C+Automation+Engineer;Welcome+To+My+Flashy+GitHub+Profile+%F0%9F%92%A5%F0%9F%9A%80">
</p>

<p align="center">
  <img src="https://i.imgur.com/zJvZ9yT.gif" width="900" />
</p>

# ⚡ About Me

Creative developer passionate about bots, automation & digital tools. I build systems for WhatsApp, Telegram & Web. 

## 🚀 Featured Projects

- [AYOMIKUN MD](${REPO_LINK_MD}) — multi-bot automation engine
- [AYOMIKUN PAIR](${REPO_LINK_PAIR}) — pairing automation system
- [AYOMIKUN TG](${REPO_LINK_TG}) — Telegram automation bot

## 📫 Contact

- Email: ${EMAIL}

—

`;

export default function App() {
  return (
    <div className="min-h-screen bg-gradient-to-br from-[#020617] via-[#0b1020] to-[#061425] text-white font-sans">
      <header className="py-10 px-6 md:px-20">
        <div className="max-w-6xl mx-auto flex flex-col md:flex-row items-center justify-between gap-6">
          <div>
            <h1 className="text-4xl md:text-5xl font-extrabold tracking-tight mb-2 neon-text">Ayo Femi <span className="text-sm align-super ml-2">(AyoFemi10)</span></h1>
            <p className="text-lg opacity-85">Developer • Automation Engineer • Bot Creator</p>
            <div className="mt-4 flex flex-wrap gap-3">
              <button onClick={downloadReadme} className="px-4 py-2 rounded-lg bg-gradient-to-r from-pink-500 to-purple-500 hover:scale-105 transform transition">Download README</button>
              <a href={`mailto:${EMAIL}`} className="px-4 py-2 rounded-lg border border-white/20 hover:bg-white/5">Contact</a>
            </div>
          </div>
          <div className="w-full md:w-1/2">
            <NeonBanner />
          </div>
        </div>
      </header>

      <main className="max-w-6xl mx-auto px-6 md:px-20 pb-20">
        <section className="mb-12">
          <h2 className="text-2xl font-bold mb-4">Featured Projects</h2>
          <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
            <ProjectCard title="AYOMIKUN MD" desc="Multi-bot automation engine for WhatsApp & web integrations." link={REPO_LINK_MD} img="https://i.imgur.com/CEhZCwT.gif"/>
            <ProjectCard title="AYOMIKUN PAIR" desc="Smart pairing automation for efficient workflows." link={REPO_LINK_PAIR} img="https://i.imgur.com/Nu8BKPb.gif"/>
            <ProjectCard title="AYOMIKUN TG" desc="Telegram automation bot with advanced utilities." link={REPO_LINK_TG} img="https://i.imgur.com/p65YqXK.gif"/>
          </div>
        </section>

        <section className="mb-12">
          <h2 className="text-2xl font-bold mb-4">GitHub Power Stats</h2>
          <div className="flex flex-col md:flex-row gap-4 items-center">
            <img src={`https://github-readme-stats.vercel.app/api?username=AyoFemi10&show_icons=true&theme=tokyonight`} alt="stats" className="rounded-lg shadow-lg"/>
            <img src={`https://github-readme-streak-stats.herokuapp.com?user=AyoFemi10&theme=tokyonight`} alt="streak" className="rounded-lg shadow-lg"/>
            <img src={`https://github-readme-stats.vercel.app/api/top-langs/?username=AyoFemi10&layout=compact&theme=tokyonight`} alt="langs" className="rounded-lg shadow-lg"/>
          </div>
        </section>

        <section className="mb-12">
          <h2 className="text-2xl font-bold mb-4">Activity & Fun</h2>
          <div className="space-y-6">
            <div className="rounded-lg overflow-hidden shadow-lg">
              <img src={`https://github-readme-activity-graph.vercel.app/graph?username=AyoFemi10&custom_title=AyoFemi10%20Activity%20Graph&bg_color=000000&color=00FFFF&line=00FFFF&point=FFFFFF&area=true`} alt="activity"/>
            </div>
            <div className="rounded-lg overflow-hidden shadow-lg">
              <img src={`https://github-readme-streak-stats.herokuapp.com?user=AyoFemi10&theme=tokyonight`} alt="snake"/>
            </div>
          </div>
        </section>

        <section className="mb-12">
          <h2 className="text-2xl font-bold mb-4">Contact</h2>
          <p>Want to collaborate? Reach me at <a href={`mailto:${EMAIL}`} className="underline">{EMAIL}</a></p>
        </section>

        <footer className="mt-20 text-center opacity-80">
          <p>Made with ❤️ by Ayo Femi — powered by imagination & code.</p>
        </footer>
      </main>

      <style>{`
        .neon-text {
          text-shadow: 0 0 8px rgba(0,255,255,0.12), 0 0 24px rgba(255,0,255,0.08), 0 0 48px rgba(255,0,255,0.06);
          background: linear-gradient(90deg,#00f7ff,#ff3ecf);
          -webkit-background-clip: text;
          -webkit-text-fill-color: transparent;
        }
        .banner-wrap { display:flex; align-items:center; justify-content:center }
      `}</style>
    </div>
  );
}

function ProjectCard({ title, desc, link, img }){
  return (
    <a href={link} target="_blank" rel="noreferrer" className="block group rounded-xl overflow-hidden transform hover:scale-105 transition shadow-2xl" style={{background: 'linear-gradient(135deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01))', border: '1px solid rgba(255,255,255,0.06)'}}>
      <div className="h-40 md:h-48 bg-black/20 flex items-center justify-center">
        <img src={img} alt={title} className="object-contain h-full w-full"/>
      </div>
      <div className="p-4 bg-gradient-to-b from-transparent to-black/40">
        <h3 className="font-bold text-lg mb-1">{title}</h3>
        <p className="text-sm opacity-80 mb-3">{desc}</p>
        <div className="flex items-center gap-2">
          <span className="px-3 py-1 rounded-full text-xs bg-white/5">Open Repo</span>
          <span className="text-xs opacity-70">• Updated recently</span>
        </div>
      </div>
    </a>
  );
}

function NeonBanner(){
  return (
    <div className="banner-wrap">
      <svg viewBox="0 0 900 220" preserveAspectRatio="xMidYMid meet" className="w-full h-40 md:h-48">
        <defs>
          <linearGradient id="g1" x1="0" x2="1">
            <stop offset="0%" stopColor="#00F7FF" />
            <stop offset="50%" stopColor="#8A2BE2" />
            <stop offset="100%" stopColor="#FF3ECF" />
          </linearGradient>

          <filter id="glow" x="-50%" y="-50%" width="200%" height="200%">
            <feGaussianBlur stdDeviation="6" result="coloredBlur" />
            <feMerge>
              <feMergeNode in="coloredBlur" />
              <feMergeNode in="SourceGraphic" />
            </feMerge>
          </filter>

        </defs>

        <rect width="100%" height="100%" rx="12" fill="rgba(0,0,0,0)" />

        <g filter="url(#glow)">
          <text x="50%" y="45%" dominantBaseline="middle" textAnchor="middle" fontFamily="'Exo 2', sans-serif" fontSize="48" fontWeight="700" fill="url(#g1)">
            AyoFemi10
          </text>

          <text x="50%" y="72%" dominantBaseline="middle" textAnchor="middle" fontFamily="monospace" fontSize="14" fill="#b2f7ff" opacity="0.8">
            Developer  •  Automation  •  Bot Creator
          </text>
        </g>

        {/* floating particles */}
        <g>
          {Array.from({length: 20}).map((_,i)=> (
            <circle key={i} cx={30 + i*40} cy={20 + (i%3)*18} r={1.6 + (i%4)*0.4} fill="#00F7FF" opacity={0.08 + (i%5)*0.03} />
          ))}
        </g>

      </svg>
    </div>
  );
}
