# PPL-```html
<!DOCTYPE html>
<html lang="en" class="h-full">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
  <meta name="theme-color" content="#02120a">
  <meta name="mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
  <meta name="description" content="Box Cricket Tournament & Practice Scoring Application">
  <title>Box Cricket League Pro</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800;900&family=Teko:wght@600;700&display=swap" rel="stylesheet">
  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            sans: ['"Plus Jakarta Sans"', 'sans-serif'],
            display: ['Teko', 'sans-serif']
          },
          colors: {
            turf: {
              950: '#02120a',
              900: '#062015',
              850: '#092b1d',
              800: '#0e3827',
              card: '#0a261a',
              border: '#154a34',
              accent: '#10b981',
              neon: '#22c55e',
              gold: '#f59e0b',
              purple: '#a855f7',
              danger: '#ef4444'
            }
          }
        }
      }
    }
  </script>
  <style>
    html, body {
      min-height: 100%;
      height: 100%;
      background-color: #02120a;
    }
    .touch-btn { touch-action: manipulation; -webkit-tap-highlight-color: transparent; }
    .touch-btn:active { transform: scale(0.96); }
    ::-webkit-scrollbar { width: 4px; height: 4px; }
    ::-webkit-scrollbar-thumb { background: #154a34; border-radius: 9999px; }
  </style>
</head>
<body class="bg-turf-950 text-slate-100 min-h-screen flex flex-col font-sans pb-24 antialiased selection:bg-emerald-500 selection:text-black">

  <!-- TOP APP BAR -->
  <header class="bg-turf-900/95 backdrop-blur-md border-b border-turf-border sticky top-0 z-40 px-3 py-2.5 shadow-xl">
    <div class="max-w-md mx-auto flex items-center justify-between">
      <div class="flex items-center space-x-2">
        <div class="w-9 h-9 rounded-xl bg-gradient-to-tr from-emerald-500 via-lime-400 to-amber-300 flex items-center justify-center text-turf-950 shadow-lg text-lg font-black">
          🏏
        </div>
        <div>
          <h1 class="text-sm font-black tracking-tight text-white flex items-center gap-1.5 leading-none">
            Box Cricket League <span id="hdrModeBadge" class="bg-amber-400 text-turf-950 text-[9px] font-black px-1.5 py-0.5 rounded shadow">TOURNAMENT</span>
          </h1>
          <p class="text-[10px] text-emerald-300/90 font-medium mt-0.5">Striker Only • 1 Ov/Player • Out (-2) • Full Stats</p>
        </div>
      </div>
      <div class="flex items-center space-x-1.5">
        <!-- Fullscreen Button -->
        <button id="btnFullscreenToggle" onclick="toggleFullScreenMode()" title="Toggle Fullscreen" class="p-2 rounded-lg bg-emerald-950 hover:bg-emerald-800 text-emerald-300 border border-emerald-700/60 shadow touch-btn">
          <svg id="iconEnterFS" class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 8V4m0 0h4M4 4l5 5m11-5h-4m4 0v4m0-4l-5 5M4 16v4m0 0h4m-4 0l5-5m11 5l-5-5m5 5v-4m0 4h-4"/></svg>
          <svg id="iconExitFS" class="w-4 h-4 hidden" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/></svg>
        </button>
        <button onclick="toggleQuickPracticeMatchModal()" title="Start Practice Match" class="px-2 py-1.5 rounded-lg bg-indigo-950 hover:bg-indigo-900 text-indigo-200 border border-indigo-700/60 shadow text-[10px] font-extrabold touch-btn flex items-center gap-1">
          <span>⚡ Practice</span>
        </button>
        <button onclick="shareScorecardWhatsApp()" title="Share Scorecard on WhatsApp" class="p-2 rounded-lg bg-emerald-950 hover:bg-emerald-800 text-emerald-300 border border-emerald-700/60 shadow touch-btn">
          <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946.003-6.556 5.338-11.891 11.893-11.891 3.181.001 6.167 1.24 8.413 3.488 2.245 2.248 3.481 5.236 3.48 8.414-.003 6.557-5.338 11.892-11.893 11.892-1.99-.001-3.951-.5-5.688-1.448l-6.305 1.654zm6.597-3.807c1.676.995 3.276 1.591 5.392 1.592 5.448 0 9.886-4.434 9.889-9.885.002-5.462-4.415-9.89-9.881-9.892-5.452 0-9.887 4.434-9.889 9.884-.001 2.225.651 3.891 1.746 5.634l-.999 3.648 3.742-.981zm11.387-5.464c-.074-.124-.272-.198-.57-.347-.297-.149-1.758-.868-2.031-.967-.272-.099-.47-.149-.669.149-.198.297-.768.967-.941 1.165-.173.198-.347.223-.644.074-.297-.149-1.255-.462-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.297-.347.446-.521.151-.172.2-.296.3-.495.099-.198.05-.372-.025-.521-.075-.148-.669-1.611-.916-2.206-.242-.579-.487-.501-.669-.51l-.57-.01c-.198 0-.52.074-.792.372s-1.04 1.016-1.04 2.479 1.065 2.876 1.213 3.074c.149.198 2.095 3.2 5.076 4.487.709.306 1.263.489 1.694.626.712.226 1.36.194 1.872.118.571-.085 1.758-.719 2.006-1.413.248-.695.248-1.29.173-1.414z"/></svg>
        </button>
        <button onclick="promptResetTournament()" title="Reset Tournament" class="p-2 rounded-lg bg-rose-950 hover:bg-rose-900 text-rose-300 border border-rose-800/60 shadow touch-btn">
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"/></svg>
        </button>
      </div>
    </div>
  </header>

  <!-- MAIN CONTAINER -->
  <main class="max-w-md mx-auto w-full px-3 pt-2.5 flex-1 space-y-3">

    <!-- Mode Alert Bar (Shown when in Practice Match) -->
    <div id="practiceModeBanner" class="hidden bg-indigo-950 border border-indigo-500 rounded-xl px-3 py-2 text-xs flex items-center justify-between text-indigo-200">
      <div class="flex items-center space-x-2">
        <span class="w-2 h-2 rounded-full bg-indigo-400 animate-ping"></span>
        <span><b>Practice Mode Active:</b> Scores won't affect tournament points table or player records.</span>
      </div>
      <button onclick="exitPracticeToTournament()" class="bg-indigo-600 hover:bg-indigo-500 text-white font-bold px-2 py-1 rounded text-[10px] touch-btn flex-shrink-0">
        Exit to League 🔙
      </button>
    </div>

    <!-- ======================================================== -->
    <!-- TAB 1: LIVE SCORER VIEW                                  -->
    <!-- ======================================================== -->
    <div id="viewScorer" class="space-y-2.5">

      <!-- Active Match Header Bar -->
      <div class="bg-turf-900 border border-turf-border rounded-xl px-3 py-1.5 flex items-center justify-between text-[11px]">
        <div class="flex items-center space-x-1.5 truncate mr-2">
          <span id="txtMatchTagBadge" class="bg-emerald-500/20 text-emerald-300 font-extrabold px-2 py-0.5 rounded border border-emerald-500/30">M1</span>
          <span id="txtMatchTypeName" class="text-slate-300 font-semibold truncate">Day 1 Match 1</span>
        </div>
        <button onclick="navigateToTab('fixtures')" class="text-amber-400 font-bold hover:underline flex items-center gap-1 flex-shrink-0 touch-btn">
          <span>Schedule 📅</span>
        </button>
      </div>

      <!-- MAIN SCOREBOARD HUD -->
      <div class="bg-turf-card border border-turf-border rounded-2xl p-3.5 shadow-2xl relative">
        <div class="flex items-center justify-between text-xs pb-2 border-b border-turf-border/60">
          <div class="flex items-center space-x-1 font-bold text-slate-200 truncate">
            <span id="labelTeam1" class="text-emerald-400 truncate max-w-[110px]">Team 1</span>
            <span class="text-slate-500 text-[10px]">vs</span>
            <span id="labelTeam2" class="text-lime-300 truncate max-w-[110px]">Team 2</span>
          </div>
          <span id="badgeInnings" class="px-2 py-0.5 rounded-full text-[10px] font-black uppercase bg-emerald-500/20 text-emerald-300 border border-emerald-500/30">
            1st Innings
          </span>
        </div>

        <div class="mt-2.5 flex items-baseline justify-between">
          <div>
            <div class="flex items-baseline space-x-2">
              <span id="scoreTotalRuns" class="font-display text-6xl font-black tracking-tight text-white leading-none">0</span>
              <span class="text-xl font-bold text-rose-400">/ <span id="scoreTotalWickets">0</span></span>
            </div>
            <p id="labelBattingTeamName" class="text-xs font-bold text-emerald-400 uppercase tracking-wider mt-1 flex items-center gap-1">
              <span>🏏 Batting:</span>
              <span class="text-white truncate max-w-[140px]">Team 1</span>
            </p>
          </div>

          <div class="text-right">
            <div class="font-display text-4xl font-bold text-slate-200 leading-none">
              <span id="scoreOversDone">0.0</span> <span class="text-xs font-sans text-slate-400">/ 5.0 Ov</span>
            </div>
            <p id="targetStatusBadge" class="text-[11px] font-bold text-amber-300 mt-1">1st Innings Live</p>
            <p id="matchCurrentRunRate" class="text-[10px] font-mono text-slate-400">CRR: 0.00</p>
          </div>
        </div>

        <!-- Over Timeline -->
        <div class="mt-2.5 pt-2 border-t border-turf-border/60">
          <div class="flex items-center justify-between text-xs mb-1">
            <span class="text-slate-300 font-semibold text-[11px]">Over <span id="currentOverIndexLabel" class="text-emerald-400 font-bold">1</span> Balls:</span>
            <span id="currentOverRunCalc" class="text-emerald-300 text-[11px] font-mono font-bold">Over Runs: 0</span>
          </div>
          <div id="ballsTimelineList" class="flex items-center space-x-1.5 overflow-x-auto py-1">
            <span class="text-slate-500 text-xs italic">Tap buttons below to record ball outcome</span>
          </div>
        </div>
      </div>

      <!-- ACTIVE STRIKER & BOWLER (WITH LIVE CHANGE BUTTONS) -->
      <div class="grid grid-cols-2 gap-2">
        <!-- Striker Card -->
        <div class="bg-turf-card border border-emerald-600/40 rounded-xl p-2.5 shadow-md">
          <div class="flex items-center justify-between mb-1">
            <div class="flex items-center space-x-1 text-emerald-400 text-[10px] font-bold uppercase tracking-wider">
              <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 animate-ping"></span>
              <span>Striker (Batter)</span>
            </div>
            <button onclick="openPlayerSelectorModal('batter')" class="text-[10px] bg-emerald-800/80 hover:bg-emerald-700 text-emerald-100 font-bold px-2 py-0.5 rounded border border-emerald-600 shadow touch-btn">
              Change ✏️
            </button>
          </div>
          <span id="txtCurrentBatterName" class="font-extrabold text-white text-xs truncate block">Player 1</span>
          <div class="mt-1 pt-1 border-t border-turf-border/40 text-xs flex justify-between font-mono">
            <span class="text-slate-300"><b id="txtBatterRuns" class="text-emerald-400 font-bold text-sm">0</b> r (<span id="txtBatterBalls">0</span>b)</span>
            <span class="text-rose-400 font-bold">Outs: <span id="txtBatterOuts">0</span> (-<span id="txtBatterPenalty">0</span>)</span>
          </div>
        </div>

        <!-- Bowler Card -->
        <div class="bg-turf-card border border-lime-600/40 rounded-xl p-2.5 shadow-md">
          <div class="flex items-center justify-between mb-1">
            <div class="flex items-center space-x-1 text-lime-400 text-[10px] font-bold uppercase tracking-wider">
              <span>🎯 Bowler</span>
            </div>
            <button onclick="openPlayerSelectorModal('bowler')" class="text-[10px] bg-lime-900/80 hover:bg-lime-800 text-lime-100 font-bold px-2 py-0.5 rounded border border-lime-600 shadow touch-btn">
              Change ✏️
            </button>
          </div>
          <span id="txtCurrentBowlerName" class="font-extrabold text-white text-xs truncate block">Player 1</span>
          <div class="mt-1 pt-1 border-t border-turf-border/40 text-xs flex justify-between font-mono">
            <span class="text-slate-300">Ov: <b id="txtBowlerBalls" class="text-lime-300">0.0</b></span>
            <span class="text-slate-300">R: <b id="txtBowlerRuns">0</b> | W: <b id="txtBowlerWickets" class="text-rose-400 font-bold">0</b></span>
          </div>
        </div>
      </div>

      <!-- SCORING BUTTONS (Custom: 0, 1, 4, 6, WD, NB, OUT -2) -->
      <div class="bg-turf-card border border-turf-border rounded-2xl p-3 shadow-2xl">
        <div class="flex items-center justify-between mb-2">
          <span class="text-xs font-black uppercase text-slate-300 tracking-wider">Scoring Actions</span>
          <span class="text-[10px] text-rose-300 font-bold bg-rose-950/70 border border-rose-800 px-2 py-0.5 rounded">Wicket = -2 Runs Penalty</span>
        </div>

        <div class="grid grid-cols-4 gap-2">
          <button onclick="recordBallAction(0)" class="touch-btn py-3 rounded-xl bg-slate-800 hover:bg-slate-700 border border-slate-700 text-white font-display text-2xl font-bold flex flex-col items-center justify-center shadow">
            <span>0</span>
            <span class="text-[9px] font-sans text-slate-400 -mt-1">Dot</span>
          </button>

          <button onclick="recordBallAction(1)" class="touch-btn py-3 rounded-xl bg-emerald-800 hover:bg-emerald-700 border border-emerald-600 text-white font-display text-2xl font-bold flex flex-col items-center justify-center shadow">
            <span>1</span>
            <span class="text-[9px] font-sans text-emerald-200 -mt-1">Single</span>
          </button>

          <button onclick="recordBallAction(4)" class="touch-btn py-3 rounded-xl bg-blue-700 hover:bg-blue-600 border border-blue-500 text-white font-display text-2xl font-bold flex flex-col items-center justify-center shadow">
            <span>4</span>
            <span class="text-[9px] font-sans text-blue-200 -mt-1">Four</span>
          </button>

          <button onclick="recordBallAction(6)" class="touch-btn py-3 rounded-xl bg-purple-700 hover:bg-purple-600 border border-purple-500 text-white font-display text-2xl font-bold flex flex-col items-center justify-center shadow">
            <span>6</span>
            <span class="text-[9px] font-sans text-purple-200 -mt-1">Six</span>
          </button>

          <button onclick="openOutDismissalModal()" class="touch-btn col-span-2 py-2.5 rounded-xl bg-gradient-to-r from-rose-700 to-red-600 hover:from-rose-600 hover:to-red-500 text-white font-black text-xs flex items-center justify-center space-x-1.5 shadow-lg border border-rose-400/50">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M6 18L18 6M6 6l12 12"/></svg>
            <span>OUT (-2 Runs Penalty)</span>
          </button>

          <button onclick="recordExtraAction('WD')" class="touch-btn py-2 rounded-xl bg-amber-700 hover:bg-amber-600 border border-amber-500 text-amber-100 font-bold text-xs flex flex-col items-center justify-center shadow">
            <span>Wide (+1)</span>
            <span class="text-[8px] font-normal text-amber-200">Extra</span>
          </button>

          <button onclick="recordExtraAction('NB')" class="touch-btn py-2 rounded-xl bg-amber-700 hover:bg-amber-600 border border-amber-500 text-amber-100 font-bold text-xs flex flex-col items-center justify-center shadow">
            <span>No Ball (+1)</span>
            <span class="text-[8px] font-normal text-amber-200">Extra</span>
          </button>
        </div>

        <div class="mt-2.5 pt-2 border-t border-turf-border/60 flex items-center justify-between gap-2">
          <button onclick="undoLastDelivery()" class="touch-btn px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 border border-slate-700 text-xs font-semibold text-slate-300 flex items-center space-x-1">
            <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 10h10a8 8 0 018 8v2M3 10l6 6m-6-6l6-6"/></svg>
            <span>Undo Ball</span>
          </button>

          <button onclick="openFullMatchScorecardModal()" class="touch-btn px-2.5 py-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 border border-slate-700 text-xs font-semibold text-amber-300 flex items-center space-x-1">
            <span>Scorecard 📋</span>
          </button>

          <button onclick="openManualOverFinishModal()" class="touch-btn px-3 py-1.5 rounded-lg bg-turf-800 hover:bg-turf-700 border border-turf-border text-xs font-semibold text-emerald-300 flex items-center space-x-1">
            <span>End Over ⏭️</span>
          </button>
        </div>
      </div>

    </div>

    <!-- ======================================================== -->
    <!-- TAB 2: SCHEDULE / FIXTURES VIEW                          -->
    <!-- ======================================================== -->
    <div id="viewFixtures" class="hidden space-y-3">
      <!-- Grand Final Spotlight -->
      <div id="finalMatchCardContainer" class="p-3.5 rounded-2xl bg-gradient-to-br from-amber-950/70 via-turf-card to-turf-900 border-2 border-amber-500/80 shadow-2xl relative overflow-hidden">
        <div class="flex items-center justify-between mb-1.5">
          <div class="flex items-center space-x-1.5">
            <span class="text-lg">👑</span>
            <span class="font-display tracking-wide text-amber-400 font-bold text-lg leading-none">GRAND FINAL (MATCH 13)</span>
          </div>
          <span id="finalMatchStatusBadge" class="text-[10px] font-black uppercase px-2 py-0.5 rounded-full bg-amber-500/20 text-amber-300 border border-amber-500/40">
            Locked
          </span>
        </div>
        <p class="text-[10px] text-slate-300">Top 1 vs Top 2 from double round-robin league stage.</p>

        <div class="mt-2.5 flex items-center justify-between text-xs font-extrabold bg-turf-950/80 p-2.5 rounded-xl border border-amber-500/30">
          <span id="txtFinalTeam1Name" class="text-amber-300 truncate max-w-[120px]">Top 1 Team</span>
          <span class="text-slate-500 text-[10px]">vs</span>
          <span id="txtFinalTeam2Name" class="text-amber-300 truncate max-w-[120px]">Top 2 Team</span>
        </div>

        <div id="finalAdvantageNotice" class="mt-2 text-[10px] text-amber-200/90 italic">
          More league wins earns Bat/Bowl selection benefit. Equal wins initiates Toss.
        </div>

        <button id="btnStartFinalMatch" onclick="handleStartFinalMatch()" disabled class="mt-2.5 w-full py-2 rounded-xl bg-slate-800 text-slate-500 font-bold text-xs border border-slate-700 cursor-not-allowed touch-btn">
          Final unlocks after 12 league matches 🔒
        </button>
      </div>

      <!-- Schedule Tabs (Day 1 vs Day 2) -->
      <div class="flex items-center justify-between pb-1">
        <h2 class="text-xs font-black uppercase text-emerald-400 tracking-wider">Tournament Schedule</h2>
        <span id="txtCompletedMatchesBadge" class="text-[10px] text-slate-400 font-mono">0 / 12 League Done</span>
      </div>

      <!-- Day 1 Schedule (6 matches) -->
      <div class="space-y-2">
        <div class="flex items-center justify-between text-xs font-extrabold text-slate-200 bg-turf-900 px-3 py-1.5 rounded-xl border border-turf-border">
          <span>DAY 1 (Leg 1 - 6 Matches)</span>
          <span class="text-[10px] text-emerald-400">Toss-Free Batting</span>
        </div>
        <div id="scheduleDay1List" class="space-y-2"></div>
      </div>

      <!-- Day 2 Schedule (6 matches + Final) -->
      <div class="space-y-2 pt-2">
        <div class="flex items-center justify-between text-xs font-extrabold text-slate-200 bg-turf-900 px-3 py-1.5 rounded-xl border border-turf-border">
          <span>DAY 2 (Leg 2 - 6 Matches Reversed)</span>
          <span class="text-[10px] text-lime-400">Batting Order Inverted</span>
        </div>
        <div id="scheduleDay2List" class="space-y-2"></div>
      </div>
    </div>

    <!-- ======================================================== -->
    <!-- TAB 3: STANDINGS & NRR                                   -->
    <!-- ======================================================== -->
    <div id="viewStandings" class="hidden space-y-3">
      <div class="bg-turf-card border border-turf-border rounded-2xl p-3 shadow-xl">
        <div class="flex items-center justify-between mb-2">
          <div>
            <h3 class="text-xs font-black uppercase text-emerald-400 tracking-wider">League Standings Table</h3>
            <p class="text-[10px] text-slate-400">Top 2 advance to the Grand Final</p>
          </div>
          <span class="text-[9px] text-amber-300 font-bold bg-amber-950/60 border border-amber-600 px-2 py-0.5 rounded">Tie-breaker: NRR</span>
        </div>

        <div class="overflow-x-auto -mx-1">
          <table class="w-full text-left text-xs whitespace-nowrap">
            <thead>
              <tr class="text-[10px] font-mono text-slate-400 border-b border-turf-border">
                <th class="py-1.5 pl-1">TEAM</th>
                <th class="py-1.5 text-center">P</th>
                <th class="py-1.5 text-center">W</th>
                <th class="py-1.5 text-center">L</th>
                <th class="py-1.5 text-center font-bold text-amber-400">PTS</th>
                <th class="py-1.5 text-center">FOR (R/O)</th>
                <th class="py-1.5 text-center">AGST (R/O)</th>
                <th class="py-1.5 pr-1 text-right font-bold text-emerald-400">NRR</th>
              </tr>
            </thead>
            <tbody id="tblStandingsBody" class="divide-y divide-turf-border/40 font-mono text-xs">
              <!-- Rendered via JS -->
            </tbody>
          </table>
        </div>
      </div>

      <!-- Match-by-match run rates -->
      <div class="bg-turf-card border border-turf-border rounded-2xl p-3 shadow-xl">
        <h4 class="text-xs font-extrabold uppercase text-slate-200 mb-2">Match-by-Match Run Rates</h4>
        <div id="matchRunRatesList" class="space-y-1.5 text-xs">
          <!-- Rendered via JS -->
        </div>
      </div>
    </div>

    <!-- ======================================================== -->
    <!-- TAB 4: LEADERBOARDS & ALL PLAYERS COMPLETE DIRECTORY     -->
    <!-- ======================================================== -->
    <div id="viewLeaderboard" class="hidden space-y-3">
      <!-- Sub-tabs for Leaderboards vs All Players Stats -->
      <div class="flex rounded-xl bg-turf-900 p-1 border border-turf-border text-xs font-bold">
        <button id="subTabBtnTrophy" onclick="switchStatsSubTab('trophy')" class="flex-1 py-1.5 rounded-lg bg-emerald-600 text-turf-950 font-black text-center touch-btn">
          Top Leaderboard 🏆
        </button>
        <button id="subTabBtnAllPlayers" onclick="switchStatsSubTab('allplayers')" class="flex-1 py-1.5 rounded-lg text-slate-400 hover:text-white text-center touch-btn">
          All Players Directory 👤
        </button>
      </div>

      <!-- Section A: Top Trophies & Caps -->
      <div id="subViewTrophies" class="space-y-3">
        <!-- BEST BATSMEN -->
        <div class="bg-turf-card border border-amber-500/50 rounded-2xl p-3 shadow-xl">
          <div class="flex items-center justify-between mb-2">
            <div class="flex items-center space-x-1.5">
              <span class="w-6 h-6 rounded-lg bg-amber-500 text-turf-950 font-black text-xs flex items-center justify-center shadow">🧢</span>
              <h3 class="text-xs font-black uppercase text-amber-400">Best Batters (Orange Cap)</h3>
            </div>
            <span class="text-[10px] text-slate-400 font-mono">Net Runs (Post -2 Penalty)</span>
          </div>
          <div id="listTopBatsmen" class="space-y-1.5 text-xs"></div>
        </div>

        <!-- BEST BOWLERS -->
        <div class="bg-turf-card border border-purple-500/50 rounded-2xl p-3 shadow-xl">
          <div class="flex items-center justify-between mb-2">
            <div class="flex items-center space-x-1.5">
              <span class="w-6 h-6 rounded-lg bg-purple-500 text-white font-black text-xs flex items-center justify-center shadow">🧢</span>
              <h3 class="text-xs font-black uppercase text-purple-300">Best Bowlers (Purple Cap)</h3>
            </div>
            <span class="text-[10px] text-slate-400 font-mono">Wickets & Economy</span>
          </div>
          <div id="listTopBowlers" class="space-y-1.5 text-xs"></div>
        </div>

        <!-- BEST FIELDERS -->
        <div class="bg-turf-card border border-blue-500/50 rounded-2xl p-3 shadow-xl">
          <div class="flex items-center justify-between mb-2">
            <div class="flex items-center space-x-1.5">
              <span class="w-6 h-6 rounded-lg bg-blue-500 text-white font-black text-xs flex items-center justify-center shadow">🧤</span>
              <h3 class="text-xs font-black uppercase text-blue-300">Best Fielders (Catches & Run Outs)</h3>
            </div>
          </div>
          <div id="listTopFielders" class="space-y-1.5 text-xs"></div>
        </div>
      </div>

      <!-- Section B: All Players Detailed Stats Directory -->
      <div id="subViewAllPlayers" class="hidden space-y-3">
        <div class="bg-turf-card border border-turf-border rounded-2xl p-3 shadow-xl">
          <div class="flex items-center justify-between mb-2">
            <h3 class="text-xs font-extrabold uppercase text-emerald-400">All 20 Players Complete Profiles</h3>
            <span class="text-[10px] text-slate-400">Batting, Bowling, Fielding</span>
          </div>
          <p class="text-[11px] text-slate-300 mb-3">View complete stats for every player across the tournament:</p>
          <div id="allPlayersStatsAccordion" class="space-y-2 text-xs"></div>
        </div>
      </div>
    </div>

    <!-- ======================================================== -->
    <!-- TAB 5: TEAMS & PLAYERS SETUP                            -->
    <!-- ======================================================== -->
    <div id="viewTeams" class="hidden space-y-3">
      <div class="bg-turf-card border border-turf-border rounded-2xl p-3 shadow-xl space-y-3">
        <div class="flex items-center justify-between">
          <h3 class="text-xs font-black uppercase text-emerald-400 tracking-wider">Manage 4 Teams (5 Players Each)</h3>
          <button onclick="saveTeamsSquads()" class="px-3 py-1 rounded-lg bg-emerald-600 hover:bg-emerald-500 text-turf-950 font-black text-xs shadow touch-btn">
            Save Rosters 💾
          </button>
        </div>
        <p class="text-[11px] text-slate-300 leading-relaxed">
          Customize team names and player names below. All schedule fixtures and stats update automatically.
        </p>

        <div id="teamSquadEditList" class="space-y-3"></div>

        <div class="pt-2 border-t border-turf-border flex justify-end">
          <button onclick="exportTournamentJSON()" class="px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 text-slate-300 text-xs font-bold border border-slate-700 touch-btn">
            Copy JSON Backup 📋
          </button>
        </div>
      </div>
    </div>

  </main>

  <!-- BOTTOM 5-TAB NAVIGATION -->
  <nav class="fixed bottom-0 left-0 right-0 bg-turf-900/95 backdrop-blur-md border-t border-turf-border z-40 px-1 py-1.5">
    <div class="max-w-md mx-auto grid grid-cols-5 gap-0.5 text-center font-bold text-[9px]">
      <button onclick="navigateToTab('fixtures')" id="tabBtnFixtures" class="flex flex-col items-center py-1 text-slate-400 hover:text-emerald-300 touch-btn">
        <svg class="w-4 h-4 mb-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"/></svg>
        <span>Schedule</span>
      </button>

      <button onclick="navigateToTab('scorer')" id="tabBtnScorer" class="flex flex-col items-center py-1 text-emerald-400 touch-btn">
        <svg class="w-4 h-4 mb-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>
        <span>Scorer</span>
      </button>

      <button onclick="navigateToTab('standings')" id="tabBtnStandings" class="flex flex-col items-center py-1 text-slate-400 hover:text-emerald-300 touch-btn">
        <svg class="w-4 h-4 mb-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"/></svg>
        <span>Standings</span>
      </button>

      <button onclick="navigateToTab('leaderboard')" id="tabBtnLeaderboard" class="flex flex-col items-center py-1 text-slate-400 hover:text-emerald-300 touch-btn">
        <svg class="w-4 h-4 mb-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"/></svg>
        <span>Records</span>
      </button>

      <button onclick="navigateToTab('teams')" id="tabBtnTeams" class="flex flex-col items-center py-1 text-slate-400 hover:text-emerald-300 touch-btn">
        <svg class="w-4 h-4 mb-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4.354a4 4 0 110 5.292M15 21H3v-1a6 6 0 0112 0v1zm0 0h6v-1a6 6 0 00-9-5.197M13 7a4 4 0 11-8 0 4 4 0 018 0z"/></svg>
        <span>Teams</span>
      </button>
    </div>
  </nav>

  <!-- ======================================================== -->
  <!-- MODAL: PRACTICE MATCH SETUP MODAL (ISOLATED)             -->
  <!-- ======================================================== -->
  <div id="practiceMatchSetupModal" class="hidden fixed inset-0 z-50 bg-black/85 flex items-center justify-center p-4">
    <div class="bg-turf-900 border-2 border-indigo-500 rounded-2xl w-full max-w-sm p-4 shadow-2xl text-slate-100">
      <div class="flex justify-between items-center pb-2 border-b border-indigo-500/40 mb-3">
        <div>
          <h3 class="text-sm font-black text-indigo-300 flex items-center gap-1.5">
            <span>⚡ Quick Practice Match</span>
          </h3>
          <p class="text-[10px] text-slate-300 mt-0.5">Completely isolated from the tournament table.</p>
        </div>
        <button onclick="toggleQuickPracticeMatchModal()" class="text-slate-400 hover:text-white text-lg font-bold touch-btn">&times;</button>
      </div>

      <div class="space-y-3 text-xs">
        <div>
          <label class="block text-slate-300 font-bold mb-1">🏏 Batting Team (Team 1):</label>
          <input type="text" id="iptPracticeTeam1" value="Practice Team A" class="w-full bg-turf-950 border border-indigo-500/60 rounded-xl p-2 text-white font-bold">
        </div>

        <div>
          <label class="block text-slate-300 font-bold mb-1">🎯 Bowling Team (Team 2):</label>
          <input type="text" id="iptPracticeTeam2" value="Practice Team B" class="w-full bg-turf-950 border border-indigo-500/60 rounded-xl p-2 text-white font-bold">
        </div>

        <div class="p-2.5 rounded-xl bg-turf-950/70 border border-indigo-500/30 text-[10px] text-indigo-200 leading-relaxed">
          ✔️ Striker only (No non-striker)<br>
          ✔️ Out applies -2 penalty runs<br>
          ✔️ 1 over per player batting & bowling<br>
          ✔️ Zero interference with tournament standings & stats.
        </div>

        <div class="pt-2 flex justify-end space-x-2">
          <button type="button" onclick="toggleQuickPracticeMatchModal()" class="px-3 py-1.5 rounded-lg bg-slate-800 text-xs font-semibold text-slate-300 touch-btn">Cancel</button>
          <button type="button" onclick="startPracticeMatchFromModal()" class="px-4 py-1.5 rounded-lg bg-indigo-600 hover:bg-indigo-500 text-white font-black text-xs shadow touch-btn">Start Match 🚀</button>
        </div>
      </div>
    </div>
  </div>

  <!-- ======================================================== -->
  <!-- MODAL: FULL MATCH SCORECARD (ALL 5 BATSMEN & BOWLERS)    -->
  <!-- ======================================================== -->
  <div id="fullScorecardModal" class="hidden fixed inset-0 z-50 bg-black/85 flex items-center justify-center p-3">
    <div class="bg-turf-900 border border-emerald-500/70 rounded-2xl w-full max-w-md max-h-[90vh] flex flex-col shadow-2xl text-slate-100 overflow-hidden">
      <div class="flex justify-between items-center p-3 border-b border-turf-border bg-turf-950">
        <div>
          <h3 id="txtScorecardTitle" class="text-sm font-black text-emerald-400">Match Full Scorecard</h3>
          <p id="txtScorecardSubtitle" class="text-[10px] text-slate-400 mt-0.5"></p>
        </div>
        <button onclick="closeFullMatchScorecardModal()" class="text-slate-400 hover:text-white text-lg font-bold touch-btn">&times;</button>
      </div>

      <div id="fullScorecardBody" class="p-3 overflow-y-auto space-y-4 text-xs">
        <!-- Rendered dynamically -->
      </div>

      <div class="p-2.5 border-t border-turf-border bg-turf-950 flex justify-between">
        <button onclick="shareScorecardWhatsApp()" class="px-3 py-1.5 rounded-xl bg-emerald-700 hover:bg-emerald-600 text-white font-bold text-xs touch-btn flex items-center gap-1 shadow">
          <span>Share WhatsApp 📲</span>
        </button>
        <button onclick="closeFullMatchScorecardModal()" class="px-4 py-1.5 rounded-xl bg-slate-800 text-slate-200 font-bold text-xs touch-btn">Close</button>
      </div>
    </div>
  </div>

  <!-- ======================================================== -->
  <!-- MODAL: EDIT FIXTURE TEAMS MODAL                          -->
  <!-- ======================================================== -->
  <div id="editFixtureModal" class="hidden fixed inset-0 z-50 bg-black/85 flex items-center justify-center p-4">
    <div class="bg-turf-900 border border-amber-500 rounded-2xl w-full max-w-sm p-4 shadow-2xl text-slate-100">
      <div class="flex justify-between items-center pb-2 border-b border-amber-500/40 mb-3">
        <div>
          <h3 id="txtEditFixtureTitle" class="text-sm font-black text-amber-400">Edit Match Teams</h3>
          <p class="text-[10px] text-slate-400 mt-0.5">Change teams or swap batting order</p>
        </div>
        <button onclick="closeEditFixtureModal()" class="text-slate-400 hover:text-white text-lg font-bold touch-btn">&times;</button>
      </div>

      <div class="space-y-3 text-xs">
        <div>
          <label class="block text-slate-300 font-bold mb-1">🏏 1st Batting Team:</label>
          <select id="selEditTeam1" class="w-full bg-turf-950 border border-turf-border rounded-xl p-2 text-white font-bold"></select>
        </div>

        <div class="flex justify-center">
          <button type="button" onclick="swapEditingTeams()" class="px-3 py-1 rounded-full bg-turf-800 hover:bg-turf-700 text-amber-300 border border-turf-border text-xs font-bold flex items-center gap-1 touch-btn">
            <span>Swap Teams ⇄</span>
          </button>
        </div>

        <div>
          <label class="block text-slate-300 font-bold mb-1">🎯 2nd Batting (Chasing) Team:</label>
          <select id="selEditTeam2" class="w-full bg-turf-950 border border-turf-border rounded-xl p-2 text-white font-bold"></select>
        </div>

        <div class="pt-2 flex justify-end space-x-2">
          <button type="button" onclick="closeEditFixtureModal()" class="px-3 py-1.5 rounded-lg bg-slate-800 text-xs font-semibold text-slate-300 touch-btn">Cancel</button>
          <button type="button" onclick="saveEditedFixtureTeams()" class="px-4 py-1.5 rounded-lg bg-amber-500 hover:bg-amber-400 text-turf-950 font-black text-xs shadow touch-btn">Update Fixture ✅</button>
        </div>
      </div>
    </div>
  </div>

  <!-- ======================================================== -->
  <!-- MODAL: SELECT / CHANGE BATTER OR BOWLER                  -->
  <!-- ======================================================== -->
  <div id="playerSelectModal" class="hidden fixed inset-0 z-50 bg-black/85 flex items-center justify-center p-4">
    <div class="bg-turf-900 border border-emerald-500 rounded-2xl w-full max-w-sm p-4 shadow-2xl text-slate-100">
      <div class="flex justify-between items-center pb-2 border-b border-turf-border mb-3">
        <div>
          <h3 id="modalPlayerSelectTitle" class="text-sm font-black text-emerald-400">Select Player</h3>
          <p id="modalPlayerSelectDesc" class="text-[10px] text-slate-400 mt-0.5">Select a player from the squad</p>
        </div>
        <button onclick="closePlayerSelectorModal()" class="text-slate-400 hover:text-white text-lg font-bold touch-btn">&times;</button>
      </div>

      <div id="modalPlayerRadioList" class="space-y-1.5 max-h-56 overflow-y-auto"></div>

      <div class="mt-4 pt-2 border-t border-turf-border flex justify-end space-x-2">
        <button type="button" onclick="closePlayerSelectorModal()" class="px-3 py-1.5 rounded-lg bg-slate-800 text-xs font-semibold text-slate-300 touch-btn">Cancel</button>
        <button type="button" onclick="confirmPlayerSelection()" class="px-4 py-1.5 rounded-lg bg-emerald-600 hover:bg-emerald-500 font-bold text-xs text-turf-950 shadow touch-btn">Confirm Selection ✅</button>
      </div>
    </div>
  </div>

  <!-- ======================================================== -->
  <!-- MODAL: WICKET DISMISSAL DETAILS (-2 PENALTY)             -->
  <!-- ======================================================== -->
  <div id="wicketDetailsModal" class="hidden fixed inset-0 z-50 bg-black/85 flex items-center justify-center p-4">
    <div class="bg-turf-900 border border-rose-500 rounded-2xl w-full max-w-sm p-4 shadow-2xl text-slate-100">
      <div class="flex justify-between items-center pb-2 border-b border-rose-500/40 mb-3">
        <div>
          <h3 class="text-sm font-black text-rose-400">Wicket Dismissal Details</h3>
          <p class="text-[10px] text-slate-400 mt-0.5">-2 penalty runs will be deducted immediately</p>
        </div>
        <button onclick="closeOutModal()" class="text-slate-400 hover:text-white text-lg font-bold touch-btn">&times;</button>
      </div>
      <div class="space-y-3 text-xs">
        <div>
          <label class="block text-slate-300 font-bold mb-1.5">How was the batter dismissed?</label>
          <div class="grid grid-cols-2 gap-1.5">
            <button type="button" onclick="setDismissalType('Bowled')" class="btn-wicket-opt py-2 px-3 rounded-lg bg-slate-800 border border-slate-700 font-bold hover:bg-emerald-800 text-left touch-btn" data-d="Bowled">Bowled</button>
            <button type="button" onclick="setDismissalType('Caught')" class="btn-wicket-opt py-2 px-3 rounded-lg bg-slate-800 border border-slate-700 font-bold hover:bg-emerald-800 text-left touch-btn" data-d="Caught">Caught</button>
            <button type="button" onclick="setDismissalType('Run Out')" class="btn-wicket-opt py-2 px-3 rounded-lg bg-slate-800 border border-slate-700 font-bold hover:bg-emerald-800 text-left touch-btn" data-d="Run Out">Run Out</button>
            <button type="button" onclick="setDismissalType('Stumped')" class="btn-wicket-opt py-2 px-3 rounded-lg bg-slate-800 border border-slate-700 font-bold hover:bg-emerald-800 text-left touch-btn" data-d="Stumped">Stumped</button>
            <button type="button" onclick="setDismissalType('Hit Wicket')" class="btn-wicket-opt col-span-2 py-2 px-3 rounded-lg bg-slate-800 border border-slate-700 font-bold hover:bg-emerald-800 text-left touch-btn" data-d="Hit Wicket">Hit Wicket</button>
          </div>
        </div>
        <div id="containerFielderSelect" class="hidden">
          <label class="block text-slate-300 font-bold mb-1">Which fielder took the catch/runout?</label>
          <select id="selFielderName" class="w-full bg-turf-950 border border-emerald-600 rounded-lg p-2 text-white font-bold"></select>
        </div>
        <div class="pt-2 flex justify-end space-x-2">
          <button type="button" onclick="closeOutModal()" class="px-3 py-1.5 rounded-lg bg-slate-800 text-xs font-semibold text-slate-300 touch-btn">Cancel</button>
          <button type="button" onclick="confirmWicketOutcome()" class="px-4 py-1.5 rounded-lg bg-rose-600 hover:bg-rose-500 font-bold text-xs text-white shadow touch-btn">Confirm Out (-2) 🛑</button>
        </div>
      </div>
    </div>
  </div>

  <!-- ======================================================== -->
  <!-- MODAL: FINAL MATCH BENEFIT / DIGITAL TOSS                -->
  <!-- ======================================================== -->
  <div id="finalSetupModal" class="hidden fixed inset-0 z-50 bg-black/90 flex items-center justify-center p-4">
    <div class="bg-turf-900 border-2 border-amber-500 rounded-2xl w-full max-w-sm p-4 text-center shadow-2xl text-slate-100">
      <div class="w-12 h-12 mx-auto rounded-full bg-amber-500/20 text-amber-400 flex items-center justify-center text-2xl mb-2">
        👑
      </div>
      <h3 class="text-base font-extrabold text-white">Grand Final: 1st Batting Decision</h3>
      <div id="finalSetupBody" class="text-xs text-slate-300 mt-2 leading-relaxed"></div>
      <div id="finalSetupActions" class="mt-4 flex flex-col gap-2"></div>
    </div>
  </div>

  <!-- ======================================================== -->
  <!-- MODAL: GENERAL NOTICE                                    -->
  <!-- ======================================================== -->
  <div id="generalNoticeModal" class="hidden fixed inset-0 z-50 bg-black/90 flex items-center justify-center p-4">
    <div class="bg-turf-900 border border-emerald-500 rounded-2xl w-full max-w-sm p-4 text-center shadow-2xl text-slate-100">
      <div id="noticeModalIcon" class="w-12 h-12 mx-auto rounded-full bg-emerald-500/20 text-emerald-400 flex items-center justify-center text-2xl mb-2">🏆</div>
      <h3 id="noticeModalTitle" class="text-base font-extrabold text-white">Notice</h3>
      <div id="noticeModalBody" class="text-xs text-slate-300 mt-2 leading-relaxed"></div>
      <div id="noticeModalActions" class="mt-4 flex flex-col gap-2"></div>
    </div>
  </div>

  <!-- JAVASCRIPT APPLICATION CODE -->
  <script>
    const LS_KEY_TEAMS = 'bcp_teams_v5';
    const LS_KEY_FIXTURES = 'bcp_fixtures_v5';
    const LS_KEY_STATS = 'bcp_stats_v5';
    const LS_KEY_ACTIVE_MATCH = 'bcp_active_match_v5';
    const LS_KEY_PRACTICE_MATCH = 'bcp_practice_match_v5';

    // Default 4 Teams with 5 Players Each
    const DEFAULT_TEAMS = [
      { id: 'T1', name: 'Team 1', players: ['Player 1', 'Player 2', 'Player 3', 'Player 4', 'Player 5'] },
      { id: 'T2', name: 'Team 2', players: ['Player 1', 'Player 2', 'Player 3', 'Player 4', 'Player 5'] },
      { id: 'T3', name: 'Team 3', players: ['Player 1', 'Player 2', 'Player 3', 'Player 4', 'Player 5'] },
      { id: 'T4', name: 'Team 4', players: ['Player 1', 'Player 2', 'Player 3', 'Player 4', 'Player 5'] }
    ];

    let tournamentTeams = [];
    let tournamentFixtures = [];
    let tournamentStats = {
      standings: {},
      batsmen: {},
      bowlers: {},
      fielders: {},
      matchRates: []
    };
    let activeMatch = null;
    let savedTournamentMatchBeforePractice = null;
    let practiceMatch = null;
    let isPracticeMode = false;

    let undoHistory = [];
    let currentDismissalChoice = 'Bowled';
    let playerSelectRole = 'batter';
    let editingFixtureId = null;

    /* =====================================================================
       FULLSCREEN API SUPPORT
       ===================================================================== */
    function toggleFullScreenMode() {
      const doc = document;
      const docEl = doc.documentElement;

      const requestFS = docEl.requestFullscreen || docEl.webkitRequestFullscreen || docEl.msRequestFullscreen;
      const exitFS = doc.exitFullscreen || doc.webkitExitFullscreen || doc.msExitFullscreen;

      const isFS = doc.fullscreenElement || doc.webkitFullscreenElement || doc.msFullscreenElement;

      if (!isFS) {
        if (requestFS) {
          requestFS.call(docEl).catch(() => {});
        }
      } else {
        if (exitFS) {
          exitFS.call(doc);
        }
      }
    }

    function updateFullscreenIconState() {
      const isFS = !!(document.fullscreenElement || document.webkitFullscreenElement || document.msFullscreenElement);
      const iconEnter = document.getElementById('iconEnterFS');
      const iconExit = document.getElementById('iconExitFS');
      if (isFS) {
        iconEnter.classList.add('hidden');
        iconExit.classList.remove('hidden');
      } else {
        iconEnter.classList.remove('hidden');
        iconExit.classList.add('hidden');
      }
    }

    document.addEventListener('fullscreenchange', updateFullscreenIconState);
    document.addEventListener('webkitfullscreenchange', updateFullscreenIconState);

    window.onload = function() {
      initAppStorage();
      renderTeamsSetupUI();
      renderFixturesList();
      renderStandingsTable();
      renderLeaderboards();

      const pm = localStorage.getItem(LS_KEY_PRACTICE_MATCH);
      if (pm) {
        practiceMatch = JSON.parse(pm);
        isPracticeMode = true;
        activeMatch = practiceMatch;
      }

      if (!activeMatch) {
        loadMatchIntoScorer(tournamentFixtures[0].matchId);
      } else {
        refreshScoringDashboard();
      }
    };

    /* =====================================================================
       SCHEDULE CREATION:
       Day 1: 6 matches (T1vT2, T3vT4, T1vT3, T2vT4, T1vT4, T2vT3)
       Day 2: 6 matches (exact reversed batting) + Match 13 (Final)
       No team plays more than 2 consecutive matches.
       ===================================================================== */
    function buildTournamentSchedule() {
      return [
        // DAY 1 (6 Matches)
        { matchId: 'M1', matchNumber: 1, day: 1, type: 'LEAGUE', title: 'Day 1 • Match 1', team1Id: 'T1', team2Id: 'T2', status: 'UPCOMING', resultText: null, matchData: null, note: 'T1 Bats First' },
        { matchId: 'M2', matchNumber: 2, day: 1, type: 'LEAGUE', title: 'Day 1 • Match 2', team1Id: 'T3', team2Id: 'T4', status: 'UPCOMING', resultText: null, matchData: null, note: 'T3 Bats First' },
        { matchId: 'M3', matchNumber: 3, day: 1, type: 'LEAGUE', title: 'Day 1 • Match 3', team1Id: 'T1', team2Id: 'T3', status: 'UPCOMING', resultText: null, matchData: null, note: 'T1 Bats First' },
        { matchId: 'M4', matchNumber: 4, day: 1, type: 'LEAGUE', title: 'Day 1 • Match 4', team1Id: 'T2', team2Id: 'T4', status: 'UPCOMING', resultText: null, matchData: null, note: 'T2 Bats First' },
        { matchId: 'M5', matchNumber: 5, day: 1, type: 'LEAGUE', title: 'Day 1 • Match 5', team1Id: 'T1', team2Id: 'T4', status: 'UPCOMING', resultText: null, matchData: null, note: 'T1 Bats First' },
        { matchId: 'M6', matchNumber: 6, day: 1, type: 'LEAGUE', title: 'Day 1 • Match 6', team1Id: 'T2', team2Id: 'T3', status: 'UPCOMING', resultText: null, matchData: null, note: 'T2 Bats First' },

        // DAY 2 (6 League Matches - Exact Reversed Batting Order)
        { matchId: 'M7', matchNumber: 7, day: 2, type: 'LEAGUE', title: 'Day 2 • Match 7', team1Id: 'T2', team2Id: 'T1', status: 'UPCOMING', resultText: null, matchData: null, note: 'T2 Bats First (Reversed)' },
        { matchId: 'M8', matchNumber: 8, day: 2, type: 'LEAGUE', title: 'Day 2 • Match 8', team1Id: 'T4', team2Id: 'T3', status: 'UPCOMING', resultText: null, matchData: null, note: 'T4 Bats First (Reversed)' },
        { matchId: 'M9', matchNumber: 9, day: 2, type: 'LEAGUE', title: 'Day 2 • Match 9', team1Id: 'T3', team2Id: 'T1', status: 'UPCOMING', resultText: null, matchData: null, note: 'T3 Bats First (Reversed)' },
        { matchId: 'M10', matchNumber: 10, day: 2, type: 'LEAGUE', title: 'Day 2 • Match 10', team1Id: 'T4', team2Id: 'T2', status: 'UPCOMING', resultText: null, matchData: null, note: 'T4 Bats First (Reversed)' },
        { matchId: 'M11', matchNumber: 11, day: 2, type: 'LEAGUE', title: 'Day 2 • Match 11', team1Id: 'T4', team2Id: 'T1', status: 'UPCOMING', resultText: null, matchData: null, note: 'T4 Bats First (Reversed)' },
        { matchId: 'M12', matchNumber: 12, day: 2, type: 'LEAGUE', title: 'Day 2 • Match 12', team1Id: 'T3', team2Id: 'T2', status: 'UPCOMING', resultText: null, matchData: null, note: 'T3 Bats First (Reversed)' },

        // DAY 2: MATCH 13 (GRAND FINAL)
        { matchId: 'M13', matchNumber: 13, day: 2, type: 'FINAL', title: '👑 Grand Final (Match 13)', team1Id: null, team2Id: null, status: 'LOCKED', resultText: null, matchData: null, note: 'Top 1 vs Top 2' }
      ];
    }

    function initAppStorage() {
      const t = localStorage.getItem(LS_KEY_TEAMS);
      tournamentTeams = t ? JSON.parse(t) : JSON.parse(JSON.stringify(DEFAULT_TEAMS));

      const f = localStorage.getItem(LS_KEY_FIXTURES);
      tournamentFixtures = f ? JSON.parse(f) : buildTournamentSchedule();

      const s = localStorage.getItem(LS_KEY_STATS);
      if (s) {
        tournamentStats = JSON.parse(s);
      } else {
        resetTournamentStats();
      }

      const m = localStorage.getItem(LS_KEY_ACTIVE_MATCH);
      if (m) activeMatch = JSON.parse(m);
    }

    function resetTournamentStats() {
      tournamentStats = {
        standings: {},
        batsmen: {},
        bowlers: {},
        fielders: {},
        matchRates: []
      };
      tournamentTeams.forEach(team => {
        tournamentStats.standings[team.id] = {
          P: 0, W: 0, L: 0, PTS: 0,
          runsFor: 0, oversForBalls: 0,
          runsAgainst: 0, oversAgainstBalls: 0
        };
        team.players.forEach(p => {
          tournamentStats.batsmen[p] = { teamId: team.id, runs: 0, balls: 0, outs: 0, b4: 0, b6: 0 };
          tournamentStats.bowlers[p] = { teamId: team.id, balls: 0, runsConceded: 0, wickets: 0 };
          tournamentStats.fielders[p] = { catches: 0, runouts: 0 };
        });
      });
      syncAllStorage();
    }

    function syncAllStorage() {
      localStorage.setItem(LS_KEY_TEAMS, JSON.stringify(tournamentTeams));
      localStorage.setItem(LS_KEY_FIXTURES, JSON.stringify(tournamentFixtures));
      localStorage.setItem(LS_KEY_STATS, JSON.stringify(tournamentStats));

      if (isPracticeMode && practiceMatch) {
        localStorage.setItem(LS_KEY_PRACTICE_MATCH, JSON.stringify(practiceMatch));
      } else {
        localStorage.removeItem(LS_KEY_PRACTICE_MATCH);
        if (activeMatch) {
          localStorage.setItem(LS_KEY_ACTIVE_MATCH, JSON.stringify(activeMatch));
        } else {
          localStorage.removeItem(LS_KEY_ACTIVE_MATCH);
        }
      }
    }

    /* =====================================================================
       PRACTICE MATCH MANAGEMENT (100% ISOLATED FROM TOURNAMENT)
       ===================================================================== */
    function toggleQuickPracticeMatchModal() {
      const modal = document.getElementById('practiceMatchSetupModal');
      modal.classList.toggle('hidden');
    }

    function startPracticeMatchFromModal() {
      const t1Name = document.getElementById('iptPracticeTeam1').value.trim() || 'Practice Team A';
      const t2Name = document.getElementById('iptPracticeTeam2').value.trim() || 'Practice Team B';

      toggleQuickPracticeMatchModal();

      if (!isPracticeMode && activeMatch) {
        savedTournamentMatchBeforePractice = JSON.parse(JSON.stringify(activeMatch));
      }

      const pTeam1 = {
        id: 'PT1',
        name: t1Name,
        players: ['Player 1', 'Player 2', 'Player 3', 'Player 4', 'Player 5']
      };
      const pTeam2 = {
        id: 'PT2',
        name: t2Name,
        players: ['Player 1', 'Player 2', 'Player 3', 'Player 4', 'Player 5']
      };

      practiceMatch = {
        fixtureId: 'PRACTICE',
        matchNumber: 'P',
        type: 'PRACTICE',
        title: '⚡ Practice Match (Isolated)',
        team1Id: 'PT1',
        team2Id: 'PT2',
        practiceTeams: [pTeam1, pTeam2],
        inningsNumber: 1,
        innings1: createCustomInningsObject('PT1', 'PT2', pTeam1, pTeam2),
        innings2: createCustomInningsObject('PT2', 'PT1', pTeam2, pTeam1),
        target: null,
        status: 'LIVE',
        winnerTeamId: null
      };

      practiceMatch.innings1.currentStriker = pTeam1.players[0];
      practiceMatch.innings1.currentBowler = pTeam2.players[0];
      practiceMatch.innings2.currentStriker = pTeam2.players[0];
      practiceMatch.innings2.currentBowler = pTeam1.players[0];

      isPracticeMode = true;
      activeMatch = practiceMatch;
      undoHistory = [];

      syncAllStorage();
      refreshScoringDashboard();
      navigateToTab('scorer');
    }

    function exitPracticeToTournament() {
      showGeneralNotice(
        'Exit Practice Match?',
        'Do you want to switch back to Tournament mode? Your active tournament fixture will be restored.',
        [
          {
            label: 'Yes, Return to Tournament',
            color: 'bg-emerald-600',
            onClick: () => {
              closeGeneralNotice();
              isPracticeMode = false;
              practiceMatch = null;
              localStorage.removeItem(LS_KEY_PRACTICE_MATCH);

              if (savedTournamentMatchBeforePractice) {
                activeMatch = savedTournamentMatchBeforePractice;
              } else {
                loadMatchIntoScorer(tournamentFixtures[0].matchId);
              }
              undoHistory = [];
              syncAllStorage();
              refreshScoringDashboard();
            }
          },
          {
            label: 'Cancel',
            color: 'bg-slate-700',
            onClick: closeGeneralNotice
          }
        ]
      );
    }

    function getTeamObjectById(teamId) {
      if (isPracticeMode && activeMatch && activeMatch.practiceTeams) {
        return activeMatch.practiceTeams.find(t => t.id === teamId) || { id: teamId, name: 'Practice Team', players: ['P1','P2','P3','P4','P5'] };
      }
      return tournamentTeams.find(t => t.id === teamId) || { id: teamId, name: 'Team', players: ['P1','P2','P3','P4','P5'] };
    }

    function createCustomInningsObject(battingTeamId, bowlingTeamId, batTeam, bowlTeam) {
      const pStats = {};
      [...batTeam.players, ...bowlTeam.players].forEach(p => {
        pStats[p] = {
          runs: 0,
          balls: 0,
          outs: 0,
          boundaries4: 0,
          boundaries6: 0,
          runsConceded: 0,
          wicketsTaken: 0,
          ballsBowled: 0
        };
      });

      return {
        battingTeamId,
        bowlingTeamId,
        totalScore: 0,
        wickets: 0,
        completedOvers: 0,
        ballsInCurrentOver: 0,
        currentStriker: batTeam.players[0],
        currentBowler: bowlTeam.players[0],
        oversData: [[], [], [], [], []],
        playerStats: pStats
      };
    }

    function getActiveInnings() {
      return activeMatch.inningsNumber === 1 ? activeMatch.innings1 : activeMatch.innings2;
    }

    function loadMatchIntoScorer(matchId, customBattingFirstId = null) {
      if (isPracticeMode) {
        isPracticeMode = false;
        practiceMatch = null;
        localStorage.removeItem(LS_KEY_PRACTICE_MATCH);
      }

      const fix = tournamentFixtures.find(f => f.matchId === matchId);
      if (!fix) return;

      if (fix.matchData) {
        activeMatch = JSON.parse(JSON.stringify(fix.matchData));
        undoHistory = [];
        syncAllStorage();
        refreshScoringDashboard();
        navigateToTab('scorer');
        return;
      }

      const batFirstId = customBattingFirstId || fix.team1Id;
      const batSecondId = (batFirstId === fix.team1Id) ? fix.team2Id : fix.team1Id;

      const batTeam = tournamentTeams.find(t => t.id === batFirstId);
      const bowlTeam = tournamentTeams.find(t => t.id === batSecondId);

      activeMatch = {
        fixtureId: fix.matchId,
        matchNumber: fix.matchNumber,
        type: fix.type,
        title: fix.title,
        team1Id: batFirstId,
        team2Id: batSecondId,
        inningsNumber: 1,
        innings1: createCustomInningsObject(batFirstId, batSecondId, batTeam, bowlTeam),
        innings2: createCustomInningsObject(batSecondId, batFirstId, bowlTeam, batTeam),
        target: null,
        status: 'LIVE',
        winnerTeamId: null
      };

      activeMatch.innings1.currentStriker = batTeam.players[0];
      activeMatch.innings1.currentBowler = bowlTeam.players[0];
      activeMatch.innings2.currentStriker = bowlTeam.players[0];
      activeMatch.innings2.currentBowler = batTeam.players[0];

      fix.status = 'LIVE';
      undoHistory = [];
      syncAllStorage();
      refreshScoringDashboard();
      renderFixturesList();
      navigateToTab('scorer');
    }

    /* =====================================================================
       LIVE BATSMAN & BOWLER SELECTION MODAL
       ===================================================================== */
    function openPlayerSelectorModal(role) {
      if (!activeMatch || activeMatch.status === 'COMPLETED') return;
      playerSelectRole = role;
      const inn = getActiveInnings();

      const modalTitle = document.getElementById('modalPlayerSelectTitle');
      const modalDesc = document.getElementById('modalPlayerSelectDesc');
      const radioContainer = document.getElementById('modalPlayerRadioList');

      let targetTeam;
      let currentSelectedPlayer;

      if (role === 'batter') {
        targetTeam = getTeamObjectById(inn.battingTeamId);
        currentSelectedPlayer = inn.currentStriker;
        modalTitle.textContent = "Select Striker (Batter)";
        modalDesc.textContent = `${targetTeam.name} batting squad:`;
      } else {
        targetTeam = getTeamObjectById(inn.bowlingTeamId);
        currentSelectedPlayer = inn.currentBowler;
        modalTitle.textContent = "Select Bowler";
        modalDesc.textContent = `${targetTeam.name} bowling squad:`;
      }

      radioContainer.innerHTML = targetTeam.players.map(pName => {
        const isChecked = pName === currentSelectedPlayer ? 'checked' : '';
        const playerStats = inn.playerStats[pName] || { runs: 0, wicketsTaken: 0 };
        return `
          <label class="flex items-center justify-between p-2.5 rounded-xl bg-turf-card border border-turf-border cursor-pointer hover:border-emerald-500">
            <div class="flex items-center space-x-2.5">
              <input type="radio" name="playerChoiceRadio" value="${pName}" ${isChecked} class="accent-emerald-500 w-4 h-4">
              <span class="font-extrabold text-xs text-white">${pName}</span>
            </div>
            <span class="text-[10px] text-slate-400 font-mono">
              ${role === 'batter' ? `${playerStats.runs} runs` : `${playerStats.wicketsTaken} wkts`}
            </span>
          </label>
        `;
      }).join('');

      document.getElementById('playerSelectModal').classList.remove('hidden');
    }

    function closePlayerSelectorModal() {
      document.getElementById('playerSelectModal').classList.add('hidden');
    }

    function confirmPlayerSelection() {
      const selected = document.querySelector('input[name="playerChoiceRadio"]:checked');
      if (!selected) {
        closePlayerSelectorModal();
        return;
      }
      takeSnapshot();
      const inn = getActiveInnings();
      if (playerSelectRole === 'batter') {
        inn.currentStriker = selected.value;
      } else {
        inn.currentBowler = selected.value;
      }
      closePlayerSelectorModal();
      syncAllStorage();
      refreshScoringDashboard();
    }

    /* =====================================================================
       SCORING ACTIONS & -2 OUT PENALTY
       ===================================================================== */
    function takeSnapshot() {
      undoHistory.push(JSON.stringify(activeMatch));
      if (undoHistory.length > 30) undoHistory.shift();
    }

    function undoLastDelivery() {
      if (undoHistory.length === 0) {
        showGeneralNotice('Cannot Undo', 'No previous ball state recorded to undo.', [{
          label: 'OK', color: 'bg-emerald-600', onClick: closeGeneralNotice
        }]);
        return;
      }
      const prev = undoHistory.pop();
      activeMatch = JSON.parse(prev);
      syncAllStorage();
      refreshScoringDashboard();
    }

    function recordBallAction(runs) {
      if (!activeMatch || activeMatch.status === 'COMPLETED') return;
      takeSnapshot();

      const inn = getActiveInnings();
      const striker = inn.currentStriker;
      const bowler = inn.currentBowler;

      inn.totalScore += runs;
      inn.playerStats[striker].runs += runs;
      inn.playerStats[striker].balls += 1;
      if (runs === 4) inn.playerStats[striker].boundaries4 += 1;
      if (runs === 6) inn.playerStats[striker].boundaries6 += 1;

      inn.playerStats[bowler].runsConceded += runs;
      inn.playerStats[bowler].ballsBowled += 1;

      const currentOverIndex = inn.completedOvers;
      if (!inn.oversData[currentOverIndex]) inn.oversData[currentOverIndex] = [];
      inn.oversData[currentOverIndex].push({
        type: 'LEGAL',
        text: runs.toString(),
        runs: runs,
        striker: striker,
        bowler: bowler,
        out: false
      });

      inn.ballsInCurrentOver += 1;
      checkProgressionAndLimits();
    }

    function recordExtraAction(type) {
      if (!activeMatch || activeMatch.status === 'COMPLETED') return;
      takeSnapshot();

      const inn = getActiveInnings();
      const bowler = inn.currentBowler;

      inn.totalScore += 1;
      inn.playerStats[bowler].runsConceded += 1;

      const currentOverIndex = inn.completedOvers;
      if (!inn.oversData[currentOverIndex]) inn.oversData[currentOverIndex] = [];
      inn.oversData[currentOverIndex].push({
        type: type,
        text: type === 'WD' ? 'Wd' : 'NB',
        runs: 1,
        striker: inn.currentStriker,
        bowler: bowler,
        out: false
      });

      checkTargetChased();
      syncAllStorage();
      refreshScoringDashboard();
    }

    function openOutDismissalModal() {
      if (!activeMatch || activeMatch.status === 'COMPLETED') return;
      currentDismissalChoice = 'Bowled';
      document.querySelectorAll('.btn-wicket-opt').forEach(b => {
        b.classList.remove('bg-rose-700', 'text-white');
        b.classList.add('bg-slate-800');
      });
      const bowledBtn = document.querySelector('[data-d="Bowled"]');
      if (bowledBtn) {
        bowledBtn.classList.add('bg-rose-700', 'text-white');
        bowledBtn.classList.remove('bg-slate-800');
      }

      const inn = getActiveInnings();
      const bowlingTeam = getTeamObjectById(inn.bowlingTeamId);
      const sel = document.getElementById('selFielderName');
      sel.innerHTML = bowlingTeam.players.map(p => `<option value="${p}">${p}</option>`).join('');

      document.getElementById('containerFielderSelect').classList.add('hidden');
      document.getElementById('wicketDetailsModal').classList.remove('hidden');
    }

    function setDismissalType(type) {
      currentDismissalChoice = type;
      document.querySelectorAll('.btn-wicket-opt').forEach(b => {
        if (b.getAttribute('data-d') === type) {
          b.classList.add('bg-rose-700', 'text-white');
          b.classList.remove('bg-slate-800');
        } else {
          b.classList.remove('bg-rose-700', 'text-white');
          b.classList.add('bg-slate-800');
        }
      });

      const container = document.getElementById('containerFielderSelect');
      if (type === 'Caught' || type === 'Run Out') {
        container.classList.remove('hidden');
      } else {
        container.classList.add('hidden');
      }
    }

    function closeOutModal() {
      document.getElementById('wicketDetailsModal').classList.add('hidden');
    }

    function confirmWicketOutcome() {
      closeOutModal();
      takeSnapshot();

      const inn = getActiveInnings();
      const striker = inn.currentStriker;
      const bowler = inn.currentBowler;
      const fielder = document.getElementById('selFielderName').value;

      // RULE: Out penalty -2 to team & batter
      inn.totalScore -= 2;
      inn.wickets += 1;
      inn.playerStats[striker].runs -= 2;
      inn.playerStats[striker].outs += 1;
      inn.playerStats[striker].balls += 1;

      inn.playerStats[bowler].ballsBowled += 1;
      if (currentDismissalChoice !== 'Run Out') {
        inn.playerStats[bowler].wicketsTaken += 1;
      }

      // Track Fielder stats only if in tournament mode
      if (!isPracticeMode) {
        if (currentDismissalChoice === 'Caught' && fielder) {
          if (!tournamentStats.fielders[fielder]) tournamentStats.fielders[fielder] = { catches: 0, runouts: 0 };
          tournamentStats.fielders[fielder].catches += 1;
        } else if (currentDismissalChoice === 'Run Out' && fielder) {
          if (!tournamentStats.fielders[fielder]) tournamentStats.fielders[fielder] = { catches: 0, runouts: 0 };
          tournamentStats.fielders[fielder].runouts += 1;
        }
      }

      const currentOverIndex = inn.completedOvers;
      if (!inn.oversData[currentOverIndex]) inn.oversData[currentOverIndex] = [];
      inn.oversData[currentOverIndex].push({
        type: 'OUT',
        text: 'W(-2)',
        runs: -2,
        striker: striker,
        bowler: bowler,
        out: true,
        dismissal: currentDismissalChoice,
        fielder: (currentDismissalChoice === 'Caught' || currentDismissalChoice === 'Run Out') ? fielder : null
      });

      inn.ballsInCurrentOver += 1;
      checkProgressionAndLimits();
    }

    function openManualOverFinishModal() {
      showGeneralNotice(
        'Finish Over Manually?',
        'Are you sure you want to conclude the current over and rotate to the next batter/bowler?',
        [
          {
            label: 'Yes, End Over',
            color: 'bg-emerald-600',
            onClick: () => {
              closeGeneralNotice();
              takeSnapshot();
              finishOverCycle();
            }
          },
          {
            label: 'Cancel',
            color: 'bg-slate-700',
            onClick: closeGeneralNotice
          }
        ]
      );
    }

    function checkProgressionAndLimits() {
      const inn = getActiveInnings();

      // Check second innings win condition
      if (activeMatch.inningsNumber === 2 && activeMatch.target !== null) {
        if (inn.totalScore >= activeMatch.target) {
          finalizeMatchConclusion(inn.battingTeamId);
          return;
        }
      }

      // Check 6 legal balls
      if (inn.ballsInCurrentOver >= 6) {
        finishOverCycle();
        return;
      }

      syncAllStorage();
      refreshScoringDashboard();
    }

    function checkTargetChased() {
      if (activeMatch.inningsNumber === 2 && activeMatch.target !== null) {
        const inn = activeMatch.innings2;
        if (inn.totalScore >= activeMatch.target) {
          finalizeMatchConclusion(inn.battingTeamId);
        }
      }
    }

    function finishOverCycle() {
      const inn = getActiveInnings();
      inn.ballsInCurrentOver = 0;
      inn.completedOvers += 1;

      // 5 overs per innings limit
      if (inn.completedOvers >= 5) {
        if (activeMatch.inningsNumber === 1) {
          triggerFirstInningsClosure();
        } else {
          triggerSecondInningsClosure();
        }
        return;
      }

      // Automatic default progression to next player in squad
      const batTeam = getTeamObjectById(inn.battingTeamId);
      const bowlTeam = getTeamObjectById(inn.bowlingTeamId);
      if (batTeam.players[inn.completedOvers]) {
        inn.currentStriker = batTeam.players[inn.completedOvers];
      }
      if (bowlTeam.players[inn.completedOvers]) {
        inn.currentBowler = bowlTeam.players[inn.completedOvers];
      }

      syncAllStorage();
      refreshScoringDashboard();

      showGeneralNotice(
        `Over ${inn.completedOvers} Completed! 🔔`,
        `Next over is starting.<br>Striker: <b>${inn.currentStriker}</b><br>Bowler: <b>${inn.currentBowler}</b><br><small class="text-emerald-300">You can adjust them anytime using the 'Change ✏️' button.</small>`,
        [{
          label: 'Start Next Over',
          color: 'bg-emerald-600',
          onClick: () => { closeGeneralNotice(); refreshScoringDashboard(); }
        }]
      );
    }

    function triggerFirstInningsClosure() {
      const target = activeMatch.innings1.totalScore + 1;
      activeMatch.target = target;
      activeMatch.inningsNumber = 2;

      syncAllStorage();
      refreshScoringDashboard();

      const bat1 = getTeamObjectById(activeMatch.innings1.battingTeamId);
      const bat2 = getTeamObjectById(activeMatch.innings2.battingTeamId);

      showGeneralNotice(
        '1st Innings Completed! 🏁',
        `<b>${bat1.name}</b> finished with <b>${activeMatch.innings1.totalScore}</b> runs (${activeMatch.innings1.wickets} wickets).<br><br>
         <b>${bat2.name}</b> needs <b>${target} runs</b> in 5 overs to win!`,
        [{
          label: 'Start 2nd Innings 🚀',
          color: 'bg-emerald-600',
          onClick: () => { closeGeneralNotice(); refreshScoringDashboard(); }
        }]
      );
    }

    function triggerSecondInningsClosure() {
      const s1 = activeMatch.innings1.totalScore;
      const s2 = activeMatch.innings2.totalScore;
      let winnerId = null;

      if (s2 > s1) {
        winnerId = activeMatch.innings2.battingTeamId;
      } else if (s1 > s2) {
        winnerId = activeMatch.innings1.battingTeamId;
      } else {
        winnerId = 'TIE';
      }

      finalizeMatchConclusion(winnerId);
    }

    /* MATCH CONCLUSION & STATS INTEGRATION */
    function finalizeMatchConclusion(winnerId) {
      activeMatch.status = 'COMPLETED';
      activeMatch.winnerTeamId = winnerId;

      if (!isPracticeMode) {
        const fix = tournamentFixtures.find(f => f.matchId === activeMatch.fixtureId);
        if (fix) {
          fix.status = 'COMPLETED';
          fix.matchData = JSON.parse(JSON.stringify(activeMatch));
          const t1 = tournamentTeams.find(t => t.id === activeMatch.innings1.battingTeamId);
          const t2 = tournamentTeams.find(t => t.id === activeMatch.innings2.battingTeamId);
          if (winnerId === 'TIE') {
            fix.resultText = `TIE: ${t1.name} ${activeMatch.innings1.totalScore} vs ${t2.name} ${activeMatch.innings2.totalScore}`;
          } else {
            const wName = tournamentTeams.find(t => t.id === winnerId)?.name;
            fix.resultText = `${wName} Won (${activeMatch.innings1.totalScore} vs ${activeMatch.innings2.totalScore})`;
          }
        }

        applyMatchStatsAndNRR(activeMatch);
        evaluateFinalMatchEligibility();

        renderFixturesList();
        renderStandingsTable();
        renderLeaderboards();
      }

      syncAllStorage();
      refreshScoringDashboard();

      const t1 = getTeamObjectById(activeMatch.innings1.battingTeamId);
      const t2 = getTeamObjectById(activeMatch.innings2.battingTeamId);
      const winMessage = winnerId === 'TIE' ? 'Match Tied (Draw)!' : `${getTeamObjectById(winnerId)?.name} Won the Match! 🏆`;

      showGeneralNotice(
        `${isPracticeMode ? '⚡ Practice' : 'Tournament'} Match Finished! 🏆`,
        `<b>${t1.name}</b>: ${activeMatch.innings1.totalScore} runs (${activeMatch.innings1.wickets} wkts)<br>
         <b>${t2.name}</b>: ${activeMatch.innings2.totalScore} runs (${activeMatch.innings2.wickets} wkts)<br><br>
         <div class="p-2 rounded-xl bg-emerald-950/80 border border-emerald-500 text-emerald-300 font-extrabold text-sm">${winMessage}</div>`,
        [
          {
            label: 'View Full Scorecard 📋',
            color: 'bg-emerald-600',
            onClick: () => { closeGeneralNotice(); openFullMatchScorecardModal(); }
          },
          {
            label: isPracticeMode ? 'Return to Tournament' : 'View Schedule',
            color: 'bg-slate-700',
            onClick: () => {
              closeGeneralNotice();
              if (isPracticeMode) {
                exitPracticeToTournament();
              } else {
                navigateToTab('fixtures');
              }
            }
          }
        ]
      );
    }

    /* NET RUN RATE & STANDINGS ENGINE */
    function applyMatchStatsAndNRR(m) {
      const inn1 = m.innings1;
      const inn2 = m.innings2;

      const inn1Balls = (inn1.completedOvers * 6) + inn1.ballsInCurrentOver;
      const inn2Balls = (inn2.completedOvers * 6) + inn2.ballsInCurrentOver;

      const inn1OversDecimal = inn1Balls / 6;
      const inn2OversDecimal = inn2Balls / 6;

      const inn1RunRate = inn1OversDecimal > 0 ? (inn1.totalScore / inn1OversDecimal) : 0;
      const inn2RunRate = inn2OversDecimal > 0 ? (inn2.totalScore / inn2OversDecimal) : 0;

      tournamentStats.matchRates.unshift({
        matchId: m.fixtureId,
        matchTitle: m.title,
        team1Name: tournamentTeams.find(t => t.id === inn1.battingTeamId)?.name,
        team1Score: inn1.totalScore,
        team1Overs: `${inn1.completedOvers}.${inn1.ballsInCurrentOver}`,
        team1RR: inn1RunRate.toFixed(2),
        team2Name: tournamentTeams.find(t => t.id === inn2.battingTeamId)?.name,
        team2Score: inn2.totalScore,
        team2Overs: `${inn2.completedOvers}.${inn2.ballsInCurrentOver}`,
        team2RR: inn2RunRate.toFixed(2)
      });

      if (m.type === 'LEAGUE') {
        const s1 = tournamentStats.standings[inn1.battingTeamId];
        const s2 = tournamentStats.standings[inn2.battingTeamId];

        if (s1 && s2) {
          s1.P += 1;
          s2.P += 1;

          s1.runsFor += inn1.totalScore;
          s1.oversForBalls += inn1Balls;
          s1.runsAgainst += inn2.totalScore;
          s1.oversAgainstBalls += inn2Balls;

          s2.runsFor += inn2.totalScore;
          s2.oversForBalls += inn2Balls;
          s2.runsAgainst += inn1.totalScore;
          s2.oversAgainstBalls += inn1Balls;

          if (m.winnerTeamId === inn1.battingTeamId) {
            s1.W += 1;
            s1.PTS += 2;
            s2.L += 1;
          } else if (m.winnerTeamId === inn2.battingTeamId) {
            s2.W += 1;
            s2.PTS += 2;
            s1.L += 1;
          } else {
            s1.PTS += 1;
            s2.PTS += 1;
          }
        }
      }

      [inn1, inn2].forEach(inn => {
        Object.keys(inn.playerStats).forEach(pName => {
          const stat = inn.playerStats[pName];
          if (!tournamentStats.batsmen[pName]) {
            tournamentStats.batsmen[pName] = { runs: 0, balls: 0, outs: 0, b4: 0, b6: 0 };
          }
          tournamentStats.batsmen[pName].runs += stat.runs;
          tournamentStats.batsmen[pName].balls += stat.balls;
          tournamentStats.batsmen[pName].outs += stat.outs;
          tournamentStats.batsmen[pName].b4 += stat.boundaries4;
          tournamentStats.batsmen[pName].b6 += stat.boundaries6;

          if (!tournamentStats.bowlers[pName]) {
            tournamentStats.bowlers[pName] = { balls: 0, runsConceded: 0, wickets: 0 };
          }
          tournamentStats.bowlers[pName].runsConceded += stat.runsConceded;
          tournamentStats.bowlers[pName].wickets += stat.wicketsTaken;
          tournamentStats.bowlers[pName].balls += stat.ballsBowled;
        });
      });
    }

    function getSortedLeagueStandings() {
      return [...tournamentTeams].map(team => {
        const s = tournamentStats.standings[team.id] || { P: 0, W: 0, L: 0, PTS: 0, runsFor: 0, oversForBalls: 0, runsAgainst: 0, oversAgainstBalls: 0 };
        
        const forOvers = s.oversForBalls / 6;
        const againstOvers = s.oversAgainstBalls / 6;

        const forRate = forOvers > 0 ? (s.runsFor / forOvers) : 0;
        const againstRate = againstOvers > 0 ? (s.runsAgainst / againstOvers) : 0;
        const nrr = forRate - againstRate;

        return {
          teamId: team.id,
          name: team.name,
          P: s.P,
          W: s.W,
          L: s.L,
          PTS: s.PTS,
          runsFor: s.runsFor,
          oversFor: (s.oversForBalls / 6).toFixed(1),
          runsAgainst: s.runsAgainst,
          oversAgainst: (s.oversAgainstBalls / 6).toFixed(1),
          forRate: forRate.toFixed(2),
          againstRate: againstRate.toFixed(2),
          nrrVal: nrr,
          nrrFormatted: (nrr > 0 ? `+${nrr.toFixed(3)}` : nrr.toFixed(3))
        };
      }).sort((a, b) => {
        if (b.PTS !== a.PTS) return b.PTS - a.PTS;
        if (b.W !== a.W) return b.W - a.W;
        return b.nrrVal - a.nrrVal;
      });
    }

    function evaluateFinalMatchEligibility() {
      const completedLeagueMatches = tournamentFixtures.filter(f => f.type === 'LEAGUE' && f.status === 'COMPLETED').length;
      const finalFix = tournamentFixtures.find(f => f.type === 'FINAL');
      if (!finalFix) return;

      const sorted = getSortedLeagueStandings();
      const top1 = sorted[0];
      const top2 = sorted[1];

      if (top1 && top2) {
        finalFix.team1Id = top1.teamId;
        finalFix.team2Id = top2.teamId;
      }

      if (completedLeagueMatches >= 12) {
        if (finalFix.status === 'LOCKED') {
          finalFix.status = 'UPCOMING';
        }
      }
    }

    /* FINAL MATCH BENEFIT / TOSS */
    function handleStartFinalMatch() {
      const finalFix = tournamentFixtures.find(f => f.type === 'FINAL');
      if (!finalFix || finalFix.status === 'LOCKED') return;

      if (finalFix.matchData) {
        loadMatchIntoScorer('M13');
        return;
      }

      const sorted = getSortedLeagueStandings();
      const top1 = sorted[0];
      const top2 = sorted[1];

      const modal = document.getElementById('finalSetupModal');
      const body = document.getElementById('finalSetupBody');
      const actions = document.getElementById('finalSetupActions');

      if (top1.W > top2.W) {
        body.innerHTML = `
          <div class="p-2 rounded-xl bg-amber-950/60 border border-amber-500/60 text-amber-200 mb-2">
            <b>${top1.name}</b> secured more league wins (${top1.W} wins vs ${top2.W} wins)!
          </div>
          <p>Therefore, <b>${top1.name}</b> gets the choice to Bat or Bowl first:</p>
        `;
        actions.innerHTML = `
          <button onclick="confirmFinalBattingChoice('${top1.teamId}', '${top2.teamId}', 'BAT')" class="w-full py-2.5 rounded-xl bg-emerald-600 text-turf-950 font-black text-xs shadow touch-btn">
            ${top1.name} 👉 Bat First
          </button>
          <button onclick="confirmFinalBattingChoice('${top1.teamId}', '${top2.teamId}', 'BOWL')" class="w-full py-2.5 rounded-xl bg-lime-600 text-turf-950 font-black text-xs shadow touch-btn">
            ${top1.name} 👉 Bowl First (Bat Second)
          </button>
        `;
      } else {
        body.innerHTML = `
          <div class="p-2 rounded-xl bg-blue-950/60 border border-blue-500/60 text-blue-200 mb-2">
            Both finalist teams have identical wins (${top1.W} wins each)!
          </div>
          <p>Spin the <b>Digital Coin Toss</b> to decide the batting selection:</p>
          <div id="coinTossDisplay" class="my-3 text-3xl font-display font-black text-amber-400">🪙</div>
        `;
        actions.innerHTML = `
          <button onclick="executeDigitalToss('${top1.teamId}', '${top2.teamId}')" class="w-full py-2.5 rounded-xl bg-amber-500 hover:bg-amber-400 text-turf-950 font-black text-xs shadow touch-btn">
            Flip Coin Toss 🪙
          </button>
        `;
      }

      modal.classList.remove('hidden');
    }

    function executeDigitalToss(t1Id, t2Id) {
      const top1Name = tournamentTeams.find(t => t.id === t1Id)?.name;
      const top2Name = tournamentTeams.find(t => t.id === t2Id)?.name;
      const coin = document.getElementById('coinTossDisplay');
      coin.classList.add('animate-spin');

      setTimeout(() => {
        coin.classList.remove('animate-spin');
        const winnerId = Math.random() < 0.5 ? t1Id : t2Id;
        const winnerName = winnerId === t1Id ? top1Name : top2Name;
        const loserId = winnerId === t1Id ? t2Id : t1Id;

        document.getElementById('finalSetupBody').innerHTML = `
          <div class="p-3 rounded-xl bg-emerald-950 border border-emerald-500 text-emerald-300 font-extrabold text-sm mb-2">
            🎉 Toss Won By: ${winnerName}
          </div>
          <p>What does <b>${winnerName}</b> choose to do?</p>
        `;

        document.getElementById('finalSetupActions').innerHTML = `
          <button onclick="confirmFinalBattingChoice('${winnerId}', '${loserId}', 'BAT')" class="w-full py-2.5 rounded-xl bg-emerald-600 text-turf-950 font-black text-xs shadow touch-btn">
            ${winnerName} 👉 Bat First
          </button>
          <button onclick="confirmFinalBattingChoice('${winnerId}', '${loserId}', 'BOWL')" class="w-full py-2.5 rounded-xl bg-lime-600 text-turf-950 font-black text-xs shadow touch-btn">
            ${winnerName} 👉 Bowl First
          </button>
        `;
      }, 700);
    }

    function confirmFinalBattingChoice(chooserId, opponentId, choice) {
      document.getElementById('finalSetupModal').classList.add('hidden');
      const battingFirstId = (choice === 'BAT') ? chooserId : opponentId;
      loadMatchIntoScorer('M13', battingFirstId);
    }

    /* =====================================================================
       SCHEDULE TEAMS EDITING MODAL
       ===================================================================== */
    function openEditFixtureModal(matchId) {
      editingFixtureId = matchId;
      const fix = tournamentFixtures.find(f => f.matchId === matchId);
      if (!fix) return;

      document.getElementById('txtEditFixtureTitle').textContent = `Edit Match ${fix.matchNumber} (${fix.matchId})`;

      const sel1 = document.getElementById('selEditTeam1');
      const sel2 = document.getElementById('selEditTeam2');

      const options = tournamentTeams.map(t => `<option value="${t.id}">${t.name}</option>`).join('');
      sel1.innerHTML = options;
      sel2.innerHTML = options;

      sel1.value = fix.team1Id;
      sel2.value = fix.team2Id;

      document.getElementById('editFixtureModal').classList.remove('hidden');
    }

    function swapEditingTeams() {
      const sel1 = document.getElementById('selEditTeam1');
      const sel2 = document.getElementById('selEditTeam2');
      const temp = sel1.value;
      sel1.value = sel2.value;
      sel2.value = temp;
    }

    function closeEditFixtureModal() {
      document.getElementById('editFixtureModal').classList.add('hidden');
      editingFixtureId = null;
    }

    function saveEditedFixtureTeams() {
      const sel1 = document.getElementById('selEditTeam1').value;
      const sel2 = document.getElementById('selEditTeam2').value;

      if (sel1 === sel2) {
        showGeneralNotice('Selection Error', 'Both teams cannot be identical. Please pick two distinct teams.', [{
          label: 'OK', color: 'bg-emerald-600', onClick: closeGeneralNotice
        }]);
        return;
      }

      const fix = tournamentFixtures.find(f => f.matchId === editingFixtureId);
      if (fix) {
        fix.team1Id = sel1;
        fix.team2Id = sel2;
        const t1Name = tournamentTeams.find(t => t.id === sel1)?.name;
        fix.note = `${t1Name} Bats First`;

        if (activeMatch && activeMatch.fixtureId === fix.matchId && activeMatch.status !== 'COMPLETED') {
          loadMatchIntoScorer(fix.matchId);
        }
      }

      closeEditFixtureModal();
      syncAllStorage();
      renderFixturesList();
      showGeneralNotice('Fixture Updated', 'Match fixture teams and batting order updated successfully! ✅', [{
        label: 'OK', color: 'bg-emerald-600', onClick: closeGeneralNotice
      }]);
    }

    /* =====================================================================
       FULL MATCH SCORECARD MODAL (INDIVIDUAL BREAKDOWN)
       ===================================================================== */
    function openFullMatchScorecardModal() {
      if (!activeMatch) return;
      const m = activeMatch;
      const t1 = getTeamObjectById(m.innings1.battingTeamId);
      const t2 = getTeamObjectById(m.innings2.battingTeamId);

      document.getElementById('txtScorecardTitle').textContent = `${m.title} - Scorecard`;
      document.getElementById('txtScorecardSubtitle').textContent = `${t1.name} vs ${t2.name} (${isPracticeMode ? 'Practice Match' : 'Tournament'})`;

      const renderInningsTable = (inn, teamBat, teamBowl, innLabel) => {
        return `
          <div class="bg-turf-950/80 border border-turf-border rounded-xl p-2.5">
            <div class="flex justify-between items-center pb-1.5 border-b border-turf-border mb-2">
              <span class="font-bold text-emerald-400 text-xs">${innLabel}: ${teamBat.name}</span>
              <span class="font-mono font-black text-white text-xs">${inn.totalScore} r / ${inn.wickets} w (${inn.completedOvers}.${inn.ballsInCurrentOver} Ov)</span>
            </div>

            <!-- Batsmen Table -->
            <div class="mb-2">
              <p class="text-[10px] text-slate-400 font-bold mb-1">Batting Breakdown (1 Over per Batter):</p>
              <table class="w-full text-left text-[11px]">
                <thead>
                  <tr class="text-slate-400 border-b border-turf-border text-[9px]">
                    <th class="py-1">Batter</th>
                    <th class="text-center">Runs</th>
                    <th class="text-center">Balls</th>
                    <th class="text-center">4s</th>
                    <th class="text-center">6s</th>
                    <th class="text-center text-rose-400">Outs (-2)</th>
                    <th class="text-right">SR</th>
                  </tr>
                </thead>
                <tbody class="divide-y divide-turf-border/30 font-mono">
                  ${teamBat.players.map(p => {
                    const st = inn.playerStats[p] || { runs: 0, balls: 0, outs: 0, boundaries4: 0, boundaries6: 0 };
                    const sr = st.balls > 0 ? ((st.runs / st.balls) * 100).toFixed(1) : '0.0';
                    return `
                      <tr>
                        <td class="py-1 font-bold text-white">${p}</td>
                        <td class="text-center font-bold text-emerald-300">${st.runs}</td>
                        <td class="text-center text-slate-300">${st.balls}</td>
                        <td class="text-center text-blue-300">${st.boundaries4}</td>
                        <td class="text-center text-purple-300">${st.boundaries6}</td>
                        <td class="text-center text-rose-400">${st.outs} (-${st.outs * 2})</td>
                        <td class="text-right text-slate-300">${sr}</td>
                      </tr>
                    `;
                  }).join('')}
                </tbody>
              </table>
            </div>

            <!-- Bowlers Table -->
            <div>
              <p class="text-[10px] text-slate-400 font-bold mb-1">Bowling Breakdown (1 Over per Bowler):</p>
              <table class="w-full text-left text-[11px]">
                <thead>
                  <tr class="text-slate-400 border-b border-turf-border text-[9px]">
                    <th class="py-1">Bowler</th>
                    <th class="text-center">Overs</th>
                    <th class="text-center">Runs</th>
                    <th class="text-center text-purple-300">Wkts</th>
                    <th class="text-right">Eco</th>
                  </tr>
                </thead>
                <tbody class="divide-y divide-turf-border/30 font-mono">
                  ${teamBowl.players.map(p => {
                    const bw = inn.playerStats[p] || { ballsBowled: 0, runsConceded: 0, wicketsTaken: 0 };
                    const ov = `${Math.floor(bw.ballsBowled / 6)}.${bw.ballsBowled % 6}`;
                    const eco = bw.ballsBowled > 0 ? ((bw.runsConceded / bw.ballsBowled) * 6).toFixed(1) : '0.0';
                    return `
                      <tr>
                        <td class="py-1 font-bold text-white">${p}</td>
                        <td class="text-center text-slate-300">${ov}</td>
                        <td class="text-center text-slate-300">${bw.runsConceded}</td>
                        <td class="text-center font-bold text-purple-300">${bw.wicketsTaken}</td>
                        <td class="text-right text-slate-300">${eco}</td>
                      </tr>
                    `;
                  }).join('')}
                </tbody>
              </table>
            </div>
          </div>
        `;
      };

      const bodyEl = document.getElementById('fullScorecardBody');
      bodyEl.innerHTML = `
        ${renderInningsTable(m.innings1, t1, t2, '1st Innings')}
        ${renderInningsTable(m.innings2, t2, t1, '2nd Innings')}
      `;

      document.getElementById('fullScorecardModal').classList.remove('hidden');
    }

    function closeFullMatchScorecardModal() {
      document.getElementById('fullScorecardModal').classList.add('hidden');
    }

    /* =====================================================================
       ALL PLAYERS DETAILED DIRECTORY & STATS VIEW
       ===================================================================== */
    function switchStatsSubTab(subTab) {
      const btnTrophy = document.getElementById('subTabBtnTrophy');
      const btnAll = document.getElementById('subTabBtnAllPlayers');
      const viewTrophy = document.getElementById('subViewTrophies');
      const viewAll = document.getElementById('subViewAllPlayers');

      if (subTab === 'trophy') {
        btnTrophy.className = 'flex-1 py-1.5 rounded-lg bg-emerald-600 text-turf-950 font-black text-center touch-btn';
        btnAll.className = 'flex-1 py-1.5 rounded-lg text-slate-400 hover:text-white text-center touch-btn';
        viewTrophy.classList.remove('hidden');
        viewAll.classList.add('hidden');
      } else {
        btnAll.className = 'flex-1 py-1.5 rounded-lg bg-emerald-600 text-turf-950 font-black text-center touch-btn';
        btnTrophy.className = 'flex-1 py-1.5 rounded-lg text-slate-400 hover:text-white text-center touch-btn';
        viewTrophy.classList.add('hidden');
        viewAll.classList.remove('hidden');
        renderAllPlayersDetailedDirectory();
      }
    }

    function renderAllPlayersDetailedDirectory() {
      const container = document.getElementById('allPlayersStatsAccordion');

      container.innerHTML = tournamentTeams.map(team => {
        return `
          <div class="border border-turf-border rounded-xl bg-turf-900 overflow-hidden">
            <div class="p-2.5 bg-turf-card flex justify-between items-center border-b border-turf-border">
              <span class="font-extrabold text-xs text-emerald-400">${team.name}</span>
              <span class="text-[10px] text-slate-400 font-mono">5 Players</span>
            </div>
            <div class="divide-y divide-turf-border/30">
              ${team.players.map(pName => {
                const b = tournamentStats.batsmen[pName] || { runs: 0, balls: 0, outs: 0, b4: 0, b6: 0 };
                const bw = tournamentStats.bowlers[pName] || { balls: 0, runsConceded: 0, wickets: 0 };
                const f = tournamentStats.fielders[pName] || { catches: 0, runouts: 0 };

                const sr = b.balls > 0 ? ((b.runs / b.balls) * 100).toFixed(1) : '0.0';
                const overs = (bw.balls / 6).toFixed(1);
                const eco = bw.balls > 0 ? ((bw.runsConceded / bw.balls) * 6).toFixed(1) : '0.0';

                return `
                  <div class="p-2.5 space-y-1.5">
                    <div class="flex justify-between items-center font-bold">
                      <span class="text-white text-xs">👤 ${pName}</span>
                      <span class="text-[10px] text-amber-300 font-mono">Net: ${b.runs} r | ${bw.wickets} w</span>
                    </div>

                    <!-- Batting stats pill -->
                    <div class="bg-turf-950/70 p-1.5 rounded-lg text-[10px] font-mono text-slate-300 flex justify-between">
                      <span class="text-emerald-400 font-bold">🏏 Batting:</span>
                      <span>${b.runs} runs (${b.balls}b)</span>
                      <span>4s: <b class="text-blue-300">${b.b4}</b> | 6s: <b class="text-purple-300">${b.b6}</b></span>
                      <span class="text-rose-400">Outs: ${b.outs} (-${b.outs * 2})</span>
                      <span>SR: ${sr}</span>
                    </div>

                    <!-- Bowling & Fielding pill -->
                    <div class="bg-turf-950/70 p-1.5 rounded-lg text-[10px] font-mono text-slate-300 flex justify-between">
                      <span class="text-lime-400 font-bold">🎯 Bowling:</span>
                      <span>${bw.wickets} wkts</span>
                      <span>${bw.runsConceded} runs (${overs} ov)</span>
                      <span>Eco: ${eco}</span>
                      <span class="text-blue-300">🧤 C:${f.catches} RO:${f.runouts}</span>
                    </div>
                  </div>
                `;
              }).join('')}
            </div>
          </div>
        `;
      }).join('');
    }

    function refreshScoringDashboard() {
      if (!activeMatch) return;
      const inn = getActiveInnings();
      const batTeam = getTeamObjectById(inn.battingTeamId);
      const bowlTeam = getTeamObjectById(inn.bowlingTeamId);

      const practiceBanner = document.getElementById('practiceModeBanner');
      const hdrModeBadge = document.getElementById('hdrModeBadge');
      if (isPracticeMode) {
        practiceBanner.classList.remove('hidden');
        hdrModeBadge.textContent = 'PRACTICE ⚡';
        hdrModeBadge.className = 'bg-indigo-400 text-turf-950 text-[9px] font-black px-1.5 py-0.5 rounded shadow';
      } else {
        practiceBanner.classList.add('hidden');
        hdrModeBadge.textContent = 'TOURNAMENT 🏆';
        hdrModeBadge.className = 'bg-amber-400 text-turf-950 text-[9px] font-black px-1.5 py-0.5 rounded shadow';
      }

      document.getElementById('txtMatchTagBadge').textContent = isPracticeMode ? 'PM' : `M${activeMatch.matchNumber}`;
      document.getElementById('txtMatchTypeName').textContent = activeMatch.title;

      document.getElementById('labelTeam1').textContent = batTeam.name;
      document.getElementById('labelTeam2').textContent = bowlTeam.name;
      document.getElementById('badgeInnings').textContent = `${activeMatch.inningsNumber === 1 ? '1st' : '2nd'} Innings`;

      document.getElementById('scoreTotalRuns').textContent = inn.totalScore;
      document.getElementById('scoreTotalWickets').textContent = inn.wickets;
      document.getElementById('labelBattingTeamName').innerHTML = `<span>🏏 Batting:</span> <span class="text-white">${batTeam.name}</span>`;
      document.getElementById('scoreOversDone').textContent = `${inn.completedOvers}.${inn.ballsInCurrentOver}`;

      const ballsCount = (inn.completedOvers * 6) + inn.ballsInCurrentOver;
      const crr = ballsCount > 0 ? ((inn.totalScore / (ballsCount / 6))).toFixed(2) : '0.00';
      document.getElementById('matchCurrentRunRate').textContent = `CRR: ${crr}`;

      const targetLabel = document.getElementById('targetStatusBadge');
      if (activeMatch.inningsNumber === 2 && activeMatch.target !== null) {
        const need = activeMatch.target - inn.totalScore;
        const totalBallsLeft = 30 - ballsCount;
        if (activeMatch.status === 'COMPLETED') {
          targetLabel.textContent = inn.totalScore >= activeMatch.target ? 'Target Chased!' : 'Match Finished';
        } else {
          targetLabel.innerHTML = `<span class="text-amber-400 font-bold">${need} r</span> / <span class="text-white">${totalBallsLeft} b</span> needed`;
        }
      } else {
        targetLabel.textContent = '1st Innings Live';
      }

      // Striker Info
      const striker = inn.currentStriker;
      const stStats = inn.playerStats[striker] || { runs: 0, balls: 0, outs: 0 };
      document.getElementById('txtCurrentBatterName').textContent = striker;
      document.getElementById('txtBatterRuns').textContent = stStats.runs;
      document.getElementById('txtBatterBalls').textContent = stStats.balls;
      document.getElementById('txtBatterOuts').textContent = stStats.outs;
      document.getElementById('txtBatterPenalty').textContent = stStats.outs * 2;

      // Bowler Info
      const bowler = inn.currentBowler;
      const bwStats = inn.playerStats[bowler] || { runsConceded: 0, wicketsTaken: 0, ballsBowled: 0 };
      document.getElementById('txtCurrentBowlerName').textContent = bowler;
      document.getElementById('txtBowlerBalls').textContent = `${Math.floor(bwStats.ballsBowled / 6)}.${bwStats.ballsBowled % 6}`;
      document.getElementById('txtBowlerRuns').textContent = bwStats.runsConceded;
      document.getElementById('txtBowlerWickets').textContent = bwStats.wicketsTaken;

      // Over timeline
      document.getElementById('currentOverIndexLabel').textContent = inn.completedOvers + 1;
      const currentOverBalls = inn.oversData[inn.completedOvers] || [];
      const overRunsSum = currentOverBalls.reduce((acc, b) => acc + (b.runs || 0), 0);
      document.getElementById('currentOverRunCalc').textContent = `Over Runs: ${overRunsSum}`;

      const timelineEl = document.getElementById('ballsTimelineList');
      if (currentOverBalls.length === 0) {
        timelineEl.innerHTML = `<span class="text-slate-500 text-xs italic">Tap buttons below to record ball outcome</span>`;
      } else {
        timelineEl.innerHTML = currentOverBalls.map(ball => {
          let badgeColor = 'bg-slate-800 text-slate-200 border-slate-700';
          if (ball.runs === 1) badgeColor = 'bg-emerald-800 text-emerald-200 border-emerald-600 font-bold';
          if (ball.runs === 4) badgeColor = 'bg-blue-800 text-blue-200 border-blue-500 font-black';
          if (ball.runs === 6) badgeColor = 'bg-purple-800 text-purple-200 border-purple-500 font-black';
          if (ball.out) badgeColor = 'bg-rose-700 text-white border-rose-500 font-black';
          if (ball.type === 'WD' || ball.type === 'NB') badgeColor = 'bg-amber-800 text-amber-100 border-amber-600';

          return `<div class="px-2.5 py-1 rounded-lg text-xs font-mono border ${badgeColor} flex-shrink-0 text-center min-w-[32px] shadow">${ball.text}</div>`;
        }).join('');
      }
    }

    function renderFixturesList() {
      const day1Container = document.getElementById('scheduleDay1List');
      const day2Container = document.getElementById('scheduleDay2List');
      const completedCount = tournamentFixtures.filter(f => f.type === 'LEAGUE' && f.status === 'COMPLETED').length;

      document.getElementById('txtCompletedMatchesBadge').textContent = `${completedCount} / 12 League Done`;

      // Final Card Setup
      const finalFix = tournamentFixtures.find(f => f.type === 'FINAL');
      const finalTeam1 = tournamentTeams.find(t => t.id === finalFix.team1Id);
      const finalTeam2 = tournamentTeams.find(t => t.id === finalFix.team2Id);
      const finalBtn = document.getElementById('btnStartFinalMatch');
      const finalStatusBadge = document.getElementById('finalMatchStatusBadge');
      const finalAdvantageNotice = document.getElementById('finalAdvantageNotice');

      if (finalTeam1 && finalTeam2) {
        document.getElementById('txtFinalTeam1Name').textContent = finalTeam1.name;
        document.getElementById('txtFinalTeam2Name').textContent = finalTeam2.name;

        const s1 = tournamentStats.standings[finalTeam1.id] || { W: 0 };
        const s2 = tournamentStats.standings[finalTeam2.id] || { W: 0 };

        if (s1.W > s2.W) {
          finalAdvantageNotice.innerHTML = `🌟 <b>${finalTeam1.name}</b> (${s1.W} wins) earns the choice to Bat or Bowl first.`;
        } else if (s2.W > s1.W) {
          finalAdvantageNotice.innerHTML = `🌟 <b>${finalTeam2.name}</b> (${s2.W} wins) earns the choice to Bat or Bowl first.`;
        } else {
          finalAdvantageNotice.innerHTML = `⚖️ Both teams tied with ${s1.W} wins. Batting decided by Coin Toss.`;
        }
      }

      if (completedCount >= 12) {
        if (finalFix.status === 'COMPLETED') {
          finalStatusBadge.textContent = 'Final Completed 🏆';
          finalBtn.disabled = false;
          finalBtn.className = 'w-full py-2 rounded-xl bg-amber-500 text-turf-950 font-black text-xs shadow-lg cursor-pointer touch-btn';
          finalBtn.textContent = 'View Final Scorecard 🏆';
        } else {
          finalStatusBadge.textContent = 'Unlocked! 🚀';
          finalBtn.disabled = false;
          finalBtn.className = 'w-full py-2 rounded-xl bg-gradient-to-r from-amber-400 to-amber-600 text-turf-950 font-black text-xs shadow-lg hover:opacity-95 cursor-pointer animate-pulse touch-btn';
          finalBtn.textContent = 'Start Grand Final 🏆';
        }
      } else {
        finalStatusBadge.textContent = `${12 - completedCount} League Matches Remaining`;
        finalBtn.disabled = true;
        finalBtn.className = 'w-full py-2 rounded-xl bg-slate-800 text-slate-500 font-bold text-xs border border-slate-700 cursor-not-allowed touch-btn';
        finalBtn.textContent = `Final unlocks after 12 league matches 🔒`;
      }

      const renderMatchCard = (fix) => {
        const t1 = tournamentTeams.find(t => t.id === fix.team1Id);
        const t2 = tournamentTeams.find(t => t.id === fix.team2Id);
        const isCurrentActive = activeMatch && activeMatch.fixtureId === fix.matchId;

        let statusBadge = `<span class="text-[9px] px-1.5 py-0.5 rounded bg-slate-800 text-slate-400 border border-slate-700">Upcoming</span>`;
        if (fix.status === 'LIVE') statusBadge = `<span class="text-[9px] px-1.5 py-0.5 rounded bg-emerald-500 text-turf-950 font-black animate-pulse">Live</span>`;
        if (fix.status === 'COMPLETED') statusBadge = `<span class="text-[9px] px-1.5 py-0.5 rounded bg-emerald-950 text-emerald-300 border border-emerald-700 font-bold">Done</span>`;

        const canEditTeams = fix.status !== 'COMPLETED';

        return `
          <div class="p-2.5 rounded-xl border ${isCurrentActive ? 'border-emerald-500 bg-turf-900 shadow-lg' : 'border-turf-border bg-turf-card'} flex items-center justify-between">
            <div class="flex-1 mr-2">
              <div class="flex items-center space-x-1.5 mb-1">
                <span class="font-mono text-[10px] text-emerald-400 font-bold">${fix.matchId}</span>
                <span class="text-[10px] text-slate-300 font-semibold">${fix.title}</span>
                ${statusBadge}
              </div>
              <div class="font-extrabold text-xs text-white flex items-center space-x-1">
                <span class="text-emerald-300 truncate max-w-[95px]">${t1.name}</span>
                <span class="text-slate-500 font-normal text-[10px]">vs</span>
                <span class="text-lime-300 truncate max-w-[95px]">${t2.name}</span>
              </div>
              <p class="text-[9px] text-emerald-400/90 font-medium mt-0.5">${fix.note || ''}</p>
              ${fix.resultText ? `<p class="text-[10px] text-amber-300 mt-1 font-semibold truncate">${fix.resultText}</p>` : ''}
            </div>

            <div class="flex flex-col space-y-1.5 flex-shrink-0">
              <button onclick="loadMatchIntoScorer('${fix.matchId}')" class="px-3 py-1.5 rounded-lg ${isCurrentActive ? 'bg-emerald-500 text-turf-950 font-black' : 'bg-turf-800 hover:bg-turf-700 text-emerald-300 border border-turf-border'} text-[11px] font-bold shadow touch-btn">
                ${fix.status === 'COMPLETED' ? 'Scorecard 📋' : (isCurrentActive ? 'Active 🏏' : 'Score ⚡')}
              </button>

              ${canEditTeams ? `
                <button onclick="openEditFixtureModal('${fix.matchId}')" class="px-2 py-1 rounded-lg bg-slate-800 hover:bg-slate-700 text-amber-300 border border-slate-700 text-[10px] font-bold shadow flex items-center justify-center gap-1 touch-btn">
                  <span>Edit ✏️</span>
                </button>
              ` : ''}
            </div>
          </div>
        `;
      };

      day1Container.innerHTML = tournamentFixtures.filter(f => f.day === 1 && f.type === 'LEAGUE').map(renderMatchCard).join('');
      day2Container.innerHTML = tournamentFixtures.filter(f => f.day === 2 && f.type === 'LEAGUE').map(renderMatchCard).join('');
    }

    function renderStandingsTable() {
      const tbody = document.getElementById('tblStandingsBody');
      const sorted = getSortedLeagueStandings();

      tbody.innerHTML = sorted.map((t, idx) => {
        const isTop2 = idx < 2;
        return `
          <tr class="hover:bg-turf-900/60 ${isTop2 ? 'bg-emerald-950/20' : ''}">
            <td class="py-2 pl-1 text-slate-100 font-bold truncate max-w-[120px] flex items-center space-x-1">
              <span class="w-4 h-4 rounded-full ${isTop2 ? 'bg-amber-400 text-turf-950 font-black' : 'bg-slate-800 text-slate-400'} text-[9px] flex items-center justify-center font-mono">${idx + 1}</span>
              <span class="truncate">${t.name}</span>
            </td>
            <td class="py-2 text-center text-slate-400">${t.P}</td>
            <td class="py-2 text-center text-emerald-400 font-bold">${t.W}</td>
            <td class="py-2 text-center text-rose-400">${t.L}</td>
            <td class="py-2 text-center text-amber-400 font-black text-xs">${t.PTS}</td>
            <td class="py-2 text-center text-[10px] text-slate-400 font-mono">${t.runsFor}/${t.oversFor}</td>
            <td class="py-2 text-center text-[10px] text-slate-400 font-mono">${t.runsAgainst}/${t.oversAgainst}</td>
            <td class="py-2 pr-1 text-right font-mono font-bold ${t.nrrVal >= 0 ? 'text-emerald-400' : 'text-rose-400'}">${t.nrrFormatted}</td>
          </tr>
        `;
      }).join('');

      const rrList = document.getElementById('matchRunRatesList');
      if (tournamentStats.matchRates.length === 0) {
        rrList.innerHTML = `<p class="text-slate-400 italic text-xs">No completed matches yet.</p>`;
      } else {
        rrList.innerHTML = tournamentStats.matchRates.map(mr => `
          <div class="p-2 rounded-xl bg-turf-900 border border-turf-border flex items-center justify-between">
            <div>
              <span class="text-[10px] text-emerald-400 font-mono font-bold block">${mr.matchTitle}</span>
              <div class="text-xs text-slate-200 mt-0.5">
                <span>${mr.team1Name}: <b>${mr.team1Score}</b> (${mr.team1Overs} ov)</span>
                <span class="text-slate-500 mx-1">vs</span>
                <span>${mr.team2Name}: <b>${mr.team2Score}</b> (${mr.team2Overs} ov)</span>
              </div>
            </div>
            <div class="text-right font-mono text-[11px]">
              <span class="text-emerald-300 font-bold block">${mr.team1RR} RR</span>
              <span class="text-lime-300 font-bold block">${mr.team2RR} RR</span>
            </div>
          </div>
        `).join('');
      }
    }

    function renderLeaderboards() {
      // 1. Orange Cap
      const bList = document.getElementById('listTopBatsmen');
      const bArr = Object.entries(tournamentStats.batsmen).map(([name, data]) => ({ name, ...data }));
      bArr.sort((a, b) => b.runs - a.runs);
      const topB = bArr.filter(b => b.balls > 0).slice(0, 5);

      if (topB.length === 0) {
        bList.innerHTML = `<p class="text-slate-400 italic text-xs">No batting data recorded yet.</p>`;
      } else {
        bList.innerHTML = topB.map((b, idx) => {
          const sr = b.balls > 0 ? ((b.runs / b.balls) * 100).toFixed(1) : '0.0';
          return `
            <div class="flex items-center justify-between p-2 rounded-xl bg-turf-900 border border-turf-border">
              <div class="flex items-center space-x-2">
                <span class="w-5 h-5 rounded-full ${idx === 0 ? 'bg-amber-400 text-turf-950 font-black' : 'bg-amber-500/20 text-amber-300 font-bold'} text-[10px] flex items-center justify-center">${idx + 1}</span>
                <span class="font-extrabold text-white text-xs">${b.name}</span>
              </div>
              <div class="text-right font-mono">
                <span class="text-amber-400 font-black text-sm">${b.runs} Runs</span>
                <span class="text-[10px] text-slate-400 block">${b.balls}b | 4s:${b.b4} 6s:${b.b6} | SR:${sr}</span>
              </div>
            </div>
          `;
        }).join('');
      }

      // 2. Purple Cap
      const bowList = document.getElementById('listTopBowlers');
      const bowArr = Object.entries(tournamentStats.bowlers).map(([name, data]) => ({ name, ...data }));
      bowArr.sort((a, b) => {
        if (b.wickets !== a.wickets) return b.wickets - a.wickets;
        return a.runsConceded - b.runsConceded;
      });
      const topBow = bowArr.filter(bw => bw.balls > 0).slice(0, 5);

      if (topBow.length === 0) {
        bowList.innerHTML = `<p class="text-slate-400 italic text-xs">No bowling data recorded yet.</p>`;
      } else {
        bowList.innerHTML = topBow.map((bw, idx) => {
          const overs = (bw.balls / 6).toFixed(1);
          const eco = bw.balls > 0 ? ((bw.runsConceded / bw.balls) * 6).toFixed(1) : '0.0';
          return `
            <div class="flex items-center justify-between p-2 rounded-xl bg-turf-900 border border-turf-border">
              <div class="flex items-center space-x-2">
                <span class="w-5 h-5 rounded-full ${idx === 0 ? 'bg-purple-500 text-white font-black' : 'bg-purple-500/20 text-purple-300 font-bold'} text-[10px] flex items-center justify-center">${idx + 1}</span>
                <span class="font-extrabold text-white text-xs">${bw.name}</span>
              </div>
              <div class="text-right font-mono">
                <span class="text-purple-300 font-black text-sm">${bw.wickets} Wkts</span>
                <span class="text-[10px] text-slate-400 block">${bw.runsConceded} r (${overs} ov) | Eco:${eco}</span>
              </div>
            </div>
          `;
        }).join('');
      }

      // 3. Best Fielders
      const fList = document.getElementById('listTopFielders');
      const fArr = Object.entries(tournamentStats.fielders).map(([name, data]) => ({ name, ...data }));
      fArr.sort((a, b) => (b.catches + b.runouts) - (a.catches + a.runouts));
      const topF = fArr.filter(f => (f.catches + f.runouts) > 0).slice(0, 5);

      if (topF.length === 0) {
        fList.innerHTML = `<p class="text-slate-400 italic text-xs">No fielding records yet.</p>`;
      } else {
        fList.innerHTML = topF.map((f, idx) => `
          <div class="flex items-center justify-between p-2 rounded-xl bg-turf-900 border border-turf-border">
            <div class="flex items-center space-x-2">
              <span class="w-5 h-5 rounded-full bg-blue-500/20 text-blue-300 font-bold text-[10px] flex items-center justify-center">${idx + 1}</span>
              <span class="font-extrabold text-white text-xs">${f.name}</span>
            </div>
            <div class="text-right font-mono text-xs">
              <span class="text-blue-300 font-bold">${f.catches} Catches</span> |
              <span class="text-amber-300 font-bold">${f.runouts} Runouts</span>
            </div>
          </div>
        `).join('');
      }
    }

    function renderTeamsSetupUI() {
      const container = document.getElementById('teamSquadEditList');
      container.innerHTML = tournamentTeams.map((team, tIdx) => `
        <div class="p-3 rounded-xl bg-turf-900 border border-turf-border">
          <div class="mb-2">
            <label class="text-[10px] uppercase font-bold text-emerald-400">Team ${tIdx + 1} Name:</label>
            <input type="text" id="iptTeamName_${team.id}" value="${team.name}" class="w-full bg-turf-950 border border-turf-border rounded-lg p-1.5 text-xs text-white font-bold mt-0.5">
          </div>
          <div>
            <label class="text-[10px] uppercase font-bold text-slate-400">5 Players Roster:</label>
            <div class="grid grid-cols-1 gap-1 mt-1">
              ${team.players.map((p, pIdx) => `
                <div class="flex items-center space-x-1.5">
                  <span class="text-[10px] font-mono text-emerald-400 w-4">${pIdx + 1}.</span>
                  <input type="text" id="iptPlayerName_${team.id}_${pIdx}" value="${p}" class="w-full bg-turf-950 border border-slate-700 rounded-md p-1 text-xs text-slate-200">
                </div>
              `).join('')}
            </div>
          </div>
        </div>
      `).join('');
    }

    function saveTeamsSquads() {
      tournamentTeams.forEach(team => {
        const nameField = document.getElementById(`iptTeamName_${team.id}`);
        if (nameField) team.name = nameField.value.trim() || team.name;

        team.players = team.players.map((_, pIdx) => {
          const pField = document.getElementById(`iptPlayerName_${team.id}_${pIdx}`);
          return pField ? (pField.value.trim() || `Player ${pIdx + 1}`) : `Player ${pIdx + 1}`;
        });
      });

      syncAllStorage();
      refreshScoringDashboard();
      renderFixturesList();
      renderStandingsTable();
      renderLeaderboards();
      showGeneralNotice('Saved Successfully', 'Team names and player rosters updated! ✅', [{
        label: 'OK', color: 'bg-emerald-600', onClick: closeGeneralNotice
      }]);
    }

    /* WHATSAPP SHARE GENERATOR */
    function shareScorecardWhatsApp() {
      if (!activeMatch) return;
      const inn1 = activeMatch.innings1;
      const inn2 = activeMatch.innings2;
      const t1 = tournamentTeams.find(t => t.id === inn1.battingTeamId);
      const t2 = tournamentTeams.find(t => t.id === inn2.battingTeamId);

      let msg = `🏏 *BOX CRICKET SCORECARD* 🏏\n`;
      msg += `📌 *${activeMatch.title}*\n`;
      msg += `━━━━━━━━━━━━━━━━━━━━━\n`;
      msg += `*1st Innings: ${t1.name}*\n`;
      msg += `Score: *${inn1.totalScore}* runs (${inn1.wickets} outs) [5.0 Ov]\n`;
      t1.players.forEach(p => {
        const st = inn1.playerStats[p] || { runs: 0, balls: 0, outs: 0 };
        msg += `• ${p}: ${st.runs} runs (${st.balls}b) [Outs: ${st.outs}]\n`;
      });

      msg += `\n*2nd Innings: ${t2.name}*\n`;
      msg += `Score: *${inn2.totalScore}* runs (${inn2.wickets} outs) [${inn2.completedOvers}.${inn2.ballsInCurrentOver} Ov]\n`;
      t2.players.forEach(p => {
        const st = inn2.playerStats[p] || { runs: 0, balls: 0, outs: 0 };
        msg += `• ${p}: ${st.runs} runs (${st.balls}b) [Outs: ${st.outs}]\n`;
      });

      if (activeMatch.winnerTeamId) {
        const winTitle = activeMatch.winnerTeamId === 'TIE' ? 'Match Tied (Draw)!' : `${tournamentTeams.find(t => t.id === activeMatch.winnerTeamId)?.name} Won the match!`;
        msg += `\n🏆 *Result:* ${winTitle}\n`;
      }
      msg += `━━━━━━━━━━━━━━━━━━━━━\nScored on Box Cricket Pro`;

      const tempArea = document.createElement("textarea");
      document.body.appendChild(tempArea);
      tempArea.value = msg;
      tempArea.select();
      document.execCommand("copy");
      document.body.removeChild(tempArea);

      window.open(`https://api.whatsapp.com/send?text=${encodeURIComponent(msg)}`, '_blank');
    }

    function navigateToTab(tabName) {
      const tabs = ['fixtures', 'scorer', 'standings', 'leaderboard', 'teams'];
      tabs.forEach(tab => {
        const view = document.getElementById('view' + tab.charAt(0).toUpperCase() + tab.slice(1));
        const btn = document.getElementById('tabBtn' + tab.charAt(0).toUpperCase() + tab.slice(1));
        if (tab === tabName) {
          view.classList.remove('hidden');
          btn.classList.remove('text-slate-400');
          btn.classList.add('text-emerald-400');
        } else {
          view.classList.add('hidden');
          btn.classList.remove('text-emerald-400');
          btn.classList.add('text-slate-400');
        }
      });

      if (tabName === 'fixtures') renderFixturesList();
      if (tabName === 'standings') renderStandingsTable();
      if (tabName === 'leaderboard') renderLeaderboards();
    }

    function showGeneralNotice(title, htmlContent, actionButtons) {
      document.getElementById('noticeModalTitle').textContent = title;
      document.getElementById('noticeModalBody').innerHTML = htmlContent;
      const btnArea = document.getElementById('noticeModalActions');
      btnArea.innerHTML = '';

      actionButtons.forEach(btnConfig => {
        const b = document.createElement('button');
        b.className = `w-full py-2.5 rounded-xl font-extrabold text-xs text-white shadow ${btnConfig.color} touch-btn`;
        b.textContent = btnConfig.label;
        b.onclick = btnConfig.onClick;
        btnArea.appendChild(b);
      });

      document.getElementById('generalNoticeModal').classList.remove('hidden');
    }

    function closeGeneralNotice() {
      document.getElementById('generalNoticeModal').classList.add('hidden');
    }

    function promptResetTournament() {
      showGeneralNotice(
        'Reset Tournament ⚠️',
        'Are you sure you want to completely reset all fixtures, Day 1 & Day 2 matches, points table, NRR, and player statistics?',
        [
          {
            label: 'Yes, Reset All',
            color: 'bg-rose-600',
            onClick: () => {
              closeGeneralNotice();
              localStorage.removeItem(LS_KEY_FIXTURES);
              localStorage.removeItem(LS_KEY_STATS);
              localStorage.removeItem(LS_KEY_ACTIVE_MATCH);
              tournamentFixtures = buildTournamentSchedule();
              resetTournamentStats();
              activeMatch = null;
              loadMatchIntoScorer(tournamentFixtures[0].matchId);
              renderFixturesList();
              renderStandingsTable();
              renderLeaderboards();
            }
          },
          {
            label: 'Cancel',
            color: 'bg-slate-700',
            onClick: closeGeneralNotice
          }
        ]
      );
    }

    function exportTournamentJSON() {
      const payload = {
        teams: tournamentTeams,
        fixtures: tournamentFixtures,
        stats: tournamentStats
      };
      const text = JSON.stringify(payload);
      const tempArea = document.createElement("textarea");
      document.body.appendChild(tempArea);
      tempArea.value = text;
      tempArea.select();
      document.execCommand("copy");
      document.body.removeChild(tempArea);
      showGeneralNotice('Data Copied', 'Tournament data backup copied to clipboard! ✅', [{
        label: 'OK', color: 'bg-emerald-600', onClick: closeGeneralNotice
      }]);
    }
  </script>
</body>
</html>
```S7-2.o