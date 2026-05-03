<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Day 01 Notes — Git & GitHub</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #0D1117;
  --bg2: #161B22;
  --bg3: #21262D;
  --border: #30363D;
  --text: #E6EDF3;
  --text2: #C9D1D9;
  --muted: #8B949E;
  --dim: #484F58;
  --green: #3FB950;
  --green-bg: #0D1F12;
  --green-border: #238636;
  --blue: #58A6FF;
  --blue-bg: #0C2340;
  --blue-border: #1F6FEB;
  --amber: #E3B341;
  --amber-bg: #1C1700;
  --amber-border: #9E6A03;
  --purple: #BC8CFF;
  --purple-bg: #1A1040;
  --purple-border: #6E40C9;
  --red: #FF7B72;
}
* { box-sizing: border-box; margin: 0; padding: 0; }
body {
  font-family: 'Inter', sans-serif;
  background: #080C10;
  color: var(--text);
  padding: 40px 20px;
  line-height: 1.7;
}
.wrap { max-width: 780px; margin: 0 auto; }

/* HEADER */
.header {
  background: var(--bg2);
  border: 0.5px solid var(--border);
  border-radius: 16px;
  padding: 28px 32px;
  margin-bottom: 20px;
  position: relative;
  overflow: hidden;
}
.header::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0; height: 3px;
  background: linear-gradient(90deg, #3FB950, #58A6FF, #BC8CFF);
}
.header-top { display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 10px; }
.day-tag { font-family: 'JetBrains Mono', monospace; font-size: 11px; color: var(--green); background: var(--green-bg); border: 0.5px solid var(--green-border); border-radius: 999px; padding: 4px 12px; }
.header h1 { font-size: 32px; font-weight: 600; margin-bottom: 6px; }
.header h1 span { color: var(--green); }
.header p { font-size: 14px; color: var(--muted); }
.toc { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 16px; padding-top: 16px; border-top: 0.5px solid var(--border); }
.toc-item { font-size: 11px; font-family: 'JetBrains Mono', monospace; color: var(--muted); background: var(--bg3); border: 0.5px solid var(--border); border-radius: 6px; padding: 3px 10px; cursor: pointer; transition: all 0.2s; }
.toc-item:hover { color: var(--blue); border-color: var(--blue-border); }

/* NOTE CARD */
.note-card {
  background: var(--bg2);
  border: 0.5px solid var(--border);
  border-radius: 14px;
  margin-bottom: 14px;
  overflow: hidden;
}
.nc-header {
  display: flex; align-items: center; gap: 10px;
  padding: 14px 20px;
  border-bottom: 0.5px solid var(--border);
  cursor: pointer;
  user-select: none;
}
.nc-num { font-family: 'JetBrains Mono', monospace; font-size: 11px; color: var(--dim); min-width: 28px; }
.nc-dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; }
.nc-title { font-size: 13px; font-weight: 500; letter-spacing: 0.04em; text-transform: uppercase; font-family: 'JetBrains Mono', monospace; flex: 1; }
.nc-arrow { font-size: 12px; color: var(--dim); transition: transform 0.2s; }
.nc-body { padding: 20px; }

/* TYPOGRAPHY */
h3 { font-size: 15px; font-weight: 600; color: var(--text); margin: 18px 0 8px; display: flex; align-items: center; gap: 8px; }
h3:first-child { margin-top: 0; }
h3::before { content: ''; width: 3px; height: 15px; border-radius: 2px; flex-shrink: 0; }
p { font-size: 14px; color: var(--muted); line-height: 1.8; margin-bottom: 10px; }
p:last-child { margin-bottom: 0; }
p b { color: var(--text2); font-weight: 500; }
strong { color: var(--text2); font-weight: 500; }

/* HIGHLIGHT BOXES */
.box { border-radius: 8px; padding: 12px 16px; margin: 10px 0; font-size: 13px; line-height: 1.7; }
.box-green { background: var(--green-bg); border-left: 3px solid var(--green); color: #4AC261; }
.box-blue { background: var(--blue-bg); border-left: 3px solid var(--blue); color: #79C0FF; }
.box-amber { background: var(--amber-bg); border-left: 3px solid var(--amber); color: var(--amber); }
.box-purple { background: var(--purple-bg); border-left: 3px solid var(--purple); color: var(--purple); }
.box-red { background: #1C0A09; border-left: 3px solid var(--red); color: var(--red); }
.box b { font-weight: 600; }
.box span { color: var(--text2); }

/* DEFINITION LIST */
.def-list { display: flex; flex-direction: column; gap: 8px; margin: 10px 0; }
.def-item { background: var(--bg); border: 0.5px solid var(--border); border-radius: 8px; padding: 12px 14px; display: flex; gap: 12px; }
.def-key { font-family: 'JetBrains Mono', monospace; font-size: 12px; font-weight: 500; min-width: 110px; flex-shrink: 0; padding-top: 1px; }
.def-val { font-size: 13px; color: var(--muted); line-height: 1.65; }
.def-val b { color: var(--text2); font-weight: 500; }

/* CODE */
.cmd { background: #010409; border: 0.5px solid var(--border); border-radius: 8px; padding: 14px 16px; margin: 10px 0; font-family: 'JetBrains Mono', monospace; font-size: 12.5px; }
.cmd-row { display: flex; gap: 10px; padding: 2px 0; flex-wrap: wrap; }
.pmt { color: var(--green); flex-shrink: 0; }
.kw { color: #FF7B72; }
.sub { color: #FFA657; }
.val { color: #A5D6FF; }
.str { color: #79C0FF; }
.cmt { color: var(--dim); font-size: 11px; }
.gi { color: var(--green); }
.inline-code { font-family: 'JetBrains Mono', monospace; font-size: 12px; color: var(--blue); background: var(--blue-bg); border: 0.5px solid var(--blue-border); border-radius: 4px; padding: 1px 6px; }

/* TWO COL */
.two-col { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin: 10px 0; }
@media(max-width:540px){ .two-col { grid-template-columns: 1fr; } }
.col-card { background: var(--bg); border: 0.5px solid var(--border); border-radius: 10px; padding: 14px 16px; }
.col-title { font-size: 13px; font-weight: 600; margin-bottom: 6px; }
.col-body { font-size: 12px; color: var(--muted); line-height: 1.7; }
.col-body b { color: var(--text2); font-weight: 500; }

/* CHEATSHEET */
.cheat { display: grid; grid-template-columns: 1fr 1fr; gap: 6px; margin: 10px 0; }
@media(max-width:480px){ .cheat { grid-template-columns: 1fr; } }
.ci { background: var(--bg); border: 0.5px solid var(--border); border-radius: 8px; padding: 9px 12px; display: flex; justify-content: space-between; align-items: center; gap: 8px; }
.ci:hover { border-color: var(--blue-border); }
.ci-cmd { font-family: 'JetBrains Mono', monospace; font-size: 11.5px; color: var(--blue); }
.ci-desc { font-size: 10px; color: var(--dim); text-align: right; }

/* DIVIDER */
.divider { border: none; border-top: 0.5px solid var(--border); margin: 16px 0; }

/* TAGS */
.tags { display: flex; flex-wrap: wrap; gap: 7px; padding-top: 14px; border-top: 0.5px solid var(--border); margin-top: 20px; }
.tag { font-size: 10px; padding: 3px 10px; border-radius: 999px; border: 0.5px solid; font-family: 'JetBrains Mono', monospace; }
.t-g { color: var(--green); border-color: var(--green-border); background: var(--green-bg); }
.t-b { color: var(--blue); border-color: var(--blue-border); background: var(--blue-bg); }
.t-a { color: var(--amber); border-color: var(--amber-border); background: var(--amber-bg); }
.t-p { color: var(--purple); border-color: var(--purple-border); background: var(--purple-bg); }

.footer { text-align: center; font-size: 11px; color: var(--dim); font-family: 'JetBrains Mono', monospace; padding: 24px 0 0; }
.footer span { color: var(--green); }
</style>
</head>
<body>
<div class="wrap">

  <!-- HEADER -->
  <div class="header">
    <div class="header-top">
      <span class="day-tag">Day 01 / 30 — Notes</span>
    </div>
    <h1><span>Git</span> & GitHub — My Notes</h1>
    <p>Personal study notes — everything I learned today in one place.</p>
    <div class="toc">
      <span class="toc-item">Version Control</span>
      <span class="toc-item">Git vs GitHub</span>
      <span class="toc-item">Core Concepts</span>
      <span class="toc-item">Setup</span>
      <span class="toc-item">Branches</span>
      <span class="toc-item">Diff / Stash / Tags</span>
      <span class="toc-item">Remote Workflow</span>
      <span class="toc-item">Fork & PR</span>
      <span class="toc-item">Advanced Concepts</span>
      <span class="toc-item">History</span>
      <span class="toc-item">Best Practices</span>
      <span class="toc-item">Git in DevOps</span>
    </div>
  </div>

  <!-- 01 VERSION CONTROL -->
  <div class="note-card">
    <div class="nc-header">
      <span class="nc-num">01</span>
      <div class="nc-dot" style="background:var(--green)"></div>
      <span class="nc-title" style="color:var(--green)">Version Control</span>
    </div>
    <div class="nc-body">
      <p>Version control is a system that <b>records every change</b> you make to your files over time. You can go back to any previous state — like an undo button that never expires.</p>
      <div class="box box-green">
        💡 <b>Analogy:</b> <span>Think of it like a video game save point. You can make risky moves and always reload from the last checkpoint.</span>
      </div>
      <h3 style="color:var(--amber)">Before Git — History</h3>
      <p>Older tools: <b>SCCS</b>, <b>CVS</b>, <b>SVN (Subversion)</b>, <b>Perforce</b> — expensive, slow, not team-friendly.</p>
      <p><b>Git was created in 2005</b> by Linus Torvalds (Linux creator) to replace all of these — free, fast, distributed.</p>
    </div>
  </div>

  <!-- 02 GIT VS GITHUB -->
  <div class="note-card">
    <div class="nc-header">
      <span class="nc-num">02</span>
      <div class="nc-dot" style="background:var(--blue)"></div>
      <span class="nc-title" style="color:var(--blue)">Git vs GitHub</span>
    </div>
    <div class="nc-body">
      <div class="two-col">
        <div class="col-card" style="border-left:3px solid var(--blue)">
          <div class="col-title" style="color:var(--blue)">Git</div>
          <div class="col-body">Software on <b>your computer</b>. Works offline. Tracks local changes. Free & open-source. Available on Windows / macOS / Linux.</div>
        </div>
        <div class="col-card" style="border-left:3px solid var(--green)">
          <div class="col-title" style="color:var(--green)">GitHub</div>
          <div class="col-body">A <b>website</b> to store repos online. Cloud backup + collaboration. Alternatives: GitLab, Bitbucket, Azure Repos.</div>
        </div>
      </div>
      <div class="box box-blue" style="margin-top:12px">
        <b>Key rule:</b> <span>Git can exist without GitHub. GitHub cannot exist without Git. Git = engine, GitHub = cloud garage.</span>
      </div>
    </div>
  </div>

  <!-- 03 CORE CONCEPTS -->
  <div class="note-card">
    <div class="nc-header">
      <span class="nc-num">03</span>
      <div class="nc-dot" style="background:var(--amber)"></div>
      <span class="nc-title" style="color:var(--amber)">Core Concepts</span>
    </div>
    <div class="nc-body">
      <div class="def-list">
        <div class="def-item">
          <span class="def-key" style="color:var(--green)">Repository</span>
          <span class="def-val">Project folder that Git tracks. Contains a hidden <b>.git</b> folder storing full history. Created with <b>git init</b>.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--blue)">Commit</span>
          <span class="def-val">A permanent snapshot/save point. Has a unique <b>hash ID</b>, your name, timestamp, and message. Can return to any commit anytime.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--amber)">Staging Area</span>
          <span class="def-val">Buffer zone before committing. Choose exactly which files to include. Edit 5 files, commit only 2 — full control.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--purple)">HEAD</span>
          <span class="def-val">A pointer that always tells Git: "this is where you are right now." Points to latest commit on current branch.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--red)">Branch</span>
          <span class="def-val">Independent copy of codebase. Work on features/fixes without touching <b>main</b>. Multiple devs can work simultaneously.</span>
        </div>
      </div>
      <div class="box box-green" style="margin-top:12px">
        💡 <b>Commits = Photos in an album.</b> <span>Each photo captures the exact state of your code at that moment. Your repo holds all photos in order, forever.</span>
      </div>
      <div class="box box-purple" style="margin-top:8px">
        💡 <b>Staging = Packing a box.</b> <span>Gather items on table (stage), review what you want, seal and send the box (commit).</span>
      </div>
    </div>
  </div>

  <!-- 04 SETUP & COMMANDS -->
  <div class="note-card">
    <div class="nc-header">
      <span class="nc-num">04</span>
      <div class="nc-dot" style="background:var(--green)"></div>
      <span class="nc-title" style="color:var(--green)">Setup & Configuration</span>
    </div>
    <div class="nc-body">
      <h3 style="color:var(--amber)"><span style="background:var(--amber)"></span>.gitignore</h3>
      <p>Files git should <b>never track</b> — add them to <span class="inline-code">.gitignore</span></p>
      
      <div class="box box-amber">
        ⚡ <b>Atomic commits:</b> <span style="color:var(--muted)">One commit = one logical change. Small + focused commits = clean history + easy rollback.</span>
      </div>
    </div>
  </div>

  <!-- 05 BRANCHES -->
  <div class="note-card">
    <div class="nc-header">
      <span class="nc-num">05</span>
      <div class="nc-dot" style="background:var(--purple)"></div>
      <span class="nc-title" style="color:var(--purple)">Branches & Merging</span>
    </div>
    <div class="nc-body">
      <div class="box box-purple">
        💡 <b>Analogy:</b> <span style="color:var(--muted)">Parallel universes — each branch is a separate timeline. Experiment freely, then merge back into main reality.</span>
      </div>

      <h3 style="color:var(--green)"><span style="background:var(--green)"></span>Merge types</h3>
      <div class="two-col">
        <div class="col-card" style="border-left:3px solid var(--green)">
          <div class="col-title" style="color:var(--green)">Fast-forward</div>
          <div class="col-body">Main has <b>no new commits</b> since branch was created. Git just moves pointer forward. No conflicts. Simple.</div>
        </div>
        <div class="col-card" style="border-left:3px solid var(--amber)">
          <div class="col-title" style="color:var(--amber)">3-way merge</div>
          <div class="col-body"><b>Both branches</b> have new commits. Git looks at 3 points — common ancestor + tips of both branches. May cause conflicts.</div>
        </div>
      </div>
      <div class="box box-amber" style="margin-top:10px">
        ⚠️ <b>Merge conflicts:</b> <span style="color:var(--muted)">Both branches edited same line. Open file, choose version manually, then git add + commit. Use VS Code merge tool.</span>
      </div>
    </div>
  </div>

  <!-- 06 DIFF STASH TAGS -->
  <div class="note-card">
    <div class="nc-header">
      <span class="nc-num">06</span>
      <div class="nc-dot" style="background:var(--amber)"></div>
      <span class="nc-title" style="color:var(--amber)">Diff, Stash & Tags</span>
    </div>
    <div class="nc-body">
      <div class="def-list">
        <div class="def-item">
          <span class="def-key" style="color:var(--amber)">git diff</span>
          <span class="def-val">Shows exactly what changed line by line. <b style="color:var(--green)">+</b> = added, <b style="color:var(--red)">−</b> = removed. Review before committing.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--purple)">git stash</span>
          <span class="def-val">Temporary clipboard for uncommitted work. Switch branches mid-task without losing progress. Pop to restore later.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--blue)">git tag</span>
          <span class="def-val">Permanent bookmark on a commit. Used to mark releases like <b>v1.0</b>, <b>v2.0</b>. Like sticky notes on commits.</span>
        </div>
      </div>
      
    </div>
  </div>

  <!-- 07 GITHUB REMOTE -->
  <div class="note-card">
    <div class="nc-header">
      <span class="nc-num">07</span>
      <div class="nc-dot" style="background:var(--red)"></div>
      <span class="nc-title" style="color:var(--red)">GitHub — Remote Workflow</span>
    </div>
    <div class="nc-body">
      <div class="box box-red">
        ⚠️ <b>SSH is mandatory.</b> <span style="color:var(--muted)">GitHub disabled password auth in 2021. Generate SSH key pair — keep private key on machine, upload public key to GitHub Settings.</span>
      </div>

      <div class="two-col" style="margin-top:10px">
        <div class="col-card" style="border-left:3px solid var(--blue)">
          <div class="col-title" style="color:var(--blue)">git fetch</div>
          <div class="col-body">Downloads changes but does <b>NOT apply</b> them. Review first, merge when ready.</div>
        </div>
        <div class="col-card" style="border-left:3px solid var(--green)">
          <div class="col-title" style="color:var(--green)">git pull</div>
          <div class="col-body">fetch + merge in <b>one step</b>. Use when you trust the remote and want to sync immediately.</div>
        </div>
      </div>
    </div>
  </div>

  <!-- 08 HISTORY -->
  <div class="note-card">
    <div class="nc-header">
      <span class="nc-num">08</span>
      <div class="nc-dot" style="background:var(--purple)"></div>
      <span class="nc-title" style="color:var(--purple)">History — Rebase & Reflog</span>
    </div>
    <div class="nc-body">
      <div class="def-list">
        <div class="def-item">
          <span class="def-key" style="color:var(--purple)">git rebase</span>
          <span class="def-val">Replays commits on top of another branch. Creates <b>clean, linear history</b> without merge commits. Use on local branches only.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--blue)">git reflog</span>
          <span class="def-val">Records <b>every HEAD movement</b>. Your safety net — recover deleted branches, bad resets, lost commits. Local only.</span>
        </div>
      </div>
      
      <div class="box box-red" style="margin-top:10px">
        ⚠️ <b>Golden rule:</b> <span style="color:var(--muted)">Never rebase shared branches. Rebase rewrites history — breaks teammates' repos. Rebase local, merge public.</span>
      </div>
    </div>
  </div>

  <!-- 09 FORK & PULL REQUEST -->
  <div class="note-card">
    <div class="nc-header">
      <span class="nc-num">09</span>
      <div class="nc-dot" style="background:var(--blue)"></div>
      <span class="nc-title" style="color:var(--blue)">Fork & Pull Request</span>
    </div>
    <div class="nc-body">
      <div class="def-list">
        <div class="def-item">
          <span class="def-key" style="color:var(--blue)">Fork</span>
          <span class="def-val">A <b>personal copy</b> of someone else's repository on your GitHub account. You can freely experiment without affecting the original project. Used in open-source contributions.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--green)">Pull Request</span>
          <span class="def-val">A request to <b>merge your changes</b> into another repo (or branch). You say: "Hey, I made changes — please review and pull them in." Core of team collaboration on GitHub.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--purple)">Code Review</span>
          <span class="def-val">Before a PR is merged, teammates <b>review the code</b> — check for bugs, suggest improvements, approve or request changes. Quality gate before merging.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--amber)">Upstream</span>
          <span class="def-val">The <b>original repo</b> you forked from. You keep your fork in sync with upstream by fetching and merging changes from it regularly.</span>
        </div>
      </div>
      <div class="box box-blue">
        💡 <b>Open Source Flow:</b> <span>Fork repo → Make changes on your fork → Open Pull Request → Maintainer reviews → Merge into original. This is how millions of developers contribute to open source.</span>
      </div>
      <div class="box box-green" style="margin-top:8px">
        💡 <b>Team Flow:</b> <span>Create feature branch → Push to remote → Open PR → Team reviews → Merge to main → Delete branch. Never push directly to main in a team project.</span>
      </div>
    </div>
  </div>

  <!-- 10 ADVANCED CONCEPTS -->
  <div class="note-card">
    <div class="nc-header">
      <span class="nc-num">10</span>
      <div class="nc-dot" style="background:var(--purple)"></div>
      <span class="nc-title" style="color:var(--purple)">Advanced Concepts</span>
    </div>
    <div class="nc-body">
      <h3 style="color:var(--purple)">Detached HEAD</h3>
      <p>Normally HEAD points to a <b>branch</b>. Detached HEAD means HEAD points directly to a <b>specific commit</b>, not a branch. You can look around but any new commits won't belong to any branch — they can be lost. Always create a new branch if you want to keep work from a detached HEAD state.</p>
      <div class="box box-amber">
        ⚠️ <span style="color:var(--muted)">If you see "You are in detached HEAD state" — don't panic. Create a new branch immediately if you want to save work: <b style="color:var(--amber)">git switch -c new-branch-name</b></span>
      </div>

      <h3 style="color:var(--blue)">Cherry-pick</h3>
      <p>Apply a <b>specific commit</b> from one branch onto another — without merging the entire branch. Useful when you want just one fix or feature from another branch, not everything in it.</p>
      <div class="box box-blue">
        💡 <span>Like picking one specific apple from a tree instead of taking the whole branch. You choose exactly which commit you want.</span>
      </div>

      <h3 style="color:var(--green)">Squash</h3>
      <p>Combine <b>multiple commits into one</b> before merging. Instead of 10 messy "WIP" commits, you squash them into one clean commit. Keeps the main branch history readable and professional.</p>

      <h3 style="color:var(--amber)">Reset types</h3>
      <div class="def-list">
        <div class="def-item">
          <span class="def-key" style="color:var(--green)">--soft</span>
          <span class="def-val">Moves HEAD back but <b>keeps changes staged</b>. Safest option — your work is not lost, just uncommitted.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--amber)">--mixed</span>
          <span class="def-val">Moves HEAD back and <b>unstages changes</b> but keeps them in working directory. Default reset behavior.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--red)">--hard</span>
          <span class="def-val"><b>Destroys all changes</b> after that commit. Working directory, staging — everything wiped. Use with extreme caution.</span>
        </div>
      </div>

      <h3 style="color:var(--red)">Distributed vs Centralized VCS</h3>
      <div class="two-col">
        <div class="col-card" style="border-left:3px solid var(--red)">
          <div class="col-title" style="color:var(--red)">Centralized (SVN)</div>
          <div class="col-body">One central server holds all history. Everyone depends on that server. <b>No internet = no work.</b> Single point of failure.</div>
        </div>
        <div class="col-card" style="border-left:3px solid var(--green)">
          <div class="col-title" style="color:var(--green)">Distributed (Git)</div>
          <div class="col-body">Every developer has a <b>full copy</b> of the entire history. Work offline. Server goes down — no problem. Faster, more reliable.</div>
        </div>
      </div>

      <h3 style="color:var(--blue)">Git Objects — How Git stores data</h3>
      <div class="def-list">
        <div class="def-item">
          <span class="def-key" style="color:var(--blue)">Blob</span>
          <span class="def-val">Stores the <b>content of a file</b>. Just the data — no filename, no metadata.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--green)">Tree</span>
          <span class="def-val">Stores a <b>directory structure</b> — filenames + pointers to blobs. Like a folder snapshot.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--amber)">Commit object</span>
          <span class="def-val">Points to a tree + stores <b>author, message, parent commit</b>. This is what you create with git commit.</span>
        </div>
      </div>
      <div class="box box-purple">
        💡 <span>Git doesn't store diffs — it stores <b>complete snapshots</b> of your project at each commit. This is why Git is so fast compared to older VCS tools.</span>
      </div>
    </div>
  </div>

  <!-- 11 BEST PRACTICES -->
  <div class="note-card">
    <div class="nc-header">
      <span class="nc-num">11</span>
      <div class="nc-dot" style="background:var(--green)"></div>
      <span class="nc-title" style="color:var(--green)">Best Practices</span>
    </div>
    <div class="nc-body">
      <h3 style="color:var(--green)">Commit message rules</h3>
      <div class="def-list">
        <div class="def-item">
          <span class="def-key" style="color:var(--green)">Good ✓</span>
          <span class="def-val"><b>"Fix login bug when email has uppercase letters"</b> — specific, clear, tells what and why.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--red)">Bad ✗</span>
          <span class="def-val"><b>"fix"</b>, <b>"update"</b>, <b>"changes"</b>, <b>"WIP"</b> — meaningless, unhelpful to anyone reading history later.</span>
        </div>
      </div>
      <div class="box box-blue" style="margin-top:8px">
        💡 <b>Conventional Commits format:</b> <span>type(scope): description — e.g. <b>feat(auth): add OAuth login</b> or <b>fix(api): handle null response</b>. Many teams follow this standard.</span>
      </div>

      <h3 style="color:var(--amber)">Branching strategies</h3>
      <div class="def-list">
        <div class="def-item">
          <span class="def-key" style="color:var(--blue)">Git Flow</span>
          <span class="def-val">Uses <b>main, develop, feature, release, hotfix</b> branches. Good for projects with scheduled releases. More complex but structured.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--green)">Trunk Based</span>
          <span class="def-val">Everyone commits to <b>main (trunk)</b> frequently with short-lived feature branches. Used by Google, Facebook. Works well with CI/CD.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--purple)">GitHub Flow</span>
          <span class="def-val">Simple: <b>main + feature branches + PRs</b>. Create branch → commit → PR → review → merge → deploy. Best for continuous delivery.</span>
        </div>
      </div>

      <h3 style="color:var(--red)">Things to NEVER do</h3>
      <div class="box box-red">
        ⚠️ <b>Never commit secrets</b> — <span style="color:var(--muted)">API keys, passwords, tokens in .env files. Once pushed to GitHub (even private), consider them compromised. Use .gitignore always.</span>
      </div>
      <div class="box box-red" style="margin-top:8px">
        ⚠️ <b>Never force push to main</b> — <span style="color:var(--muted)">git push --force rewrites remote history. Destroys teammates' work. Only force push on your own private feature branches.</span>
      </div>
      <div class="box box-amber" style="margin-top:8px">
        ⚡ <b>Never commit node_modules / build folders</b> — <span style="color:var(--muted)">These are generated files, often hundreds of MBs. Always add them to .gitignore. Commit only source code.</span>
      </div>
    </div>
  </div>

  <!-- 12 GIT IN DEVOPS -->
  <div class="note-card">
    <div class="nc-header">
      <span class="nc-num">12</span>
      <div class="nc-dot" style="background:var(--amber)"></div>
      <span class="nc-title" style="color:var(--amber)">Git in DevOps</span>
    </div>
    <div class="nc-body">
      <p>Git is the <b>foundation of all DevOps pipelines</b>. Every push to GitHub can trigger automated processes — this is the heart of modern software delivery.</p>

      <h3 style="color:var(--green)">Git → CI/CD Pipeline</h3>
      <div class="def-list">
        <div class="def-item">
          <span class="def-key" style="color:var(--green)">git push</span>
          <span class="def-val">Triggers the entire CI/CD pipeline automatically — tests run, code is built, and deployed. <b>One push = automated delivery.</b></span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--blue)">GitHub Actions</span>
          <span class="def-val">GitHub's built-in CI/CD tool. Define workflows in <b>.yml files</b> inside .github/workflows/. Runs on every push, PR, or schedule.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--purple)">Webhooks</span>
          <span class="def-val">GitHub sends an <b>HTTP notification</b> to external tools (Jenkins, ArgoCD) when events happen — push, PR open, merge, etc.</span>
        </div>
      </div>

      <h3 style="color:var(--blue)">GitOps</h3>
      <p>A modern DevOps practice where <b>Git is the single source of truth</b> for infrastructure and application state. Everything — code, config, infrastructure — is version controlled in Git. Tools like ArgoCD or Flux watch your Git repo and automatically sync changes to Kubernetes clusters.</p>
      <div class="box box-blue">
        💡 <b>GitOps principle:</b> <span>If it's not in Git, it doesn't exist. Want to change something in production? Commit it to Git — the system applies it automatically.</span>
      </div>

      <h3 style="color:var(--amber)">Git in the DevOps toolchain</h3>
      <div class="def-list">
        <div class="def-item">
          <span class="def-key" style="color:var(--green)">Source Control</span>
          <span class="def-val">GitHub / GitLab — store all application code, Dockerfiles, Helm charts, Terraform configs.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--blue)">CI Trigger</span>
          <span class="def-val">Push to branch → Jenkins / GitHub Actions picks it up → runs tests, builds Docker image.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--purple)">CD Trigger</span>
          <span class="def-val">Merge to main → ArgoCD / Spinnaker deploys new version to Kubernetes automatically.</span>
        </div>
        <div class="def-item">
          <span class="def-key" style="color:var(--amber)">IaC Versioning</span>
          <span class="def-val">Terraform, Ansible, Kubernetes YAML files — all versioned in Git. Infrastructure changes go through PR review like code.</span>
        </div>
      </div>

      <div class="box box-green" style="margin-top:8px">
        🚀 <b>Big picture:</b> <span>Git is not just for code — in DevOps, it controls everything. Code, configs, infrastructure, pipelines, docs — all in Git. Master Git = master DevOps foundation.</span>
      </div>
    </div>
  </div>

  <!-- TAGS 
  <div class="tags">
    <span class="tag t-g">#30DaysOfDevOps</span>
    <span class="tag t-g">#Day1</span>
    <span class="tag t-b">#Git</span>
    <span class="tag t-b">#GitHub</span>
    <span class="tag t-a">#VersionControl</span>
    <span class="tag t-a">#DevOps</span>
    <span class="tag t-p">#100DaysOfCode</span>
    <span class="tag t-p">#LearnInPublic</span>
  </div>
-->
  <div class="footer">day_01 notes — <span>#30DaysOfDevOps</span> — git & github complete ✓</div>
</div>
</body>
</html>
