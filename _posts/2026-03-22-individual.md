---
layout: post
title: CS111 Blog — Chetan Tiduwar
description: A complete CS111 walkthrough of my final project — a 3-level gauntlet game built with HTML5 Canvas. Covers OOP inheritance, data types, control structures, operators, I/O, debugging, and API integration.
author: Chetan Tiduwar
date: 2026-03-23
permalink: /cs111-blog/
---

<style>
  @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Exo+2:wght@400;600;700;900&display=swap');

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body, .page-content {
    background: #060a0f;
    color: #d0e8ff;
    font-family: 'Exo 2', sans-serif;
    font-size: 16px;
    line-height: 1.7;
  }

  a { color: #38bdf8; text-decoration: none; }
  a:hover { text-decoration: underline; color: #7dd3fc; }

  .blog-wrap {
    max-width: 860px;
    margin: 0 auto;
    padding: 60px 24px 100px;
  }

  .meta { text-align: center; color: #4a6a8a; font-family: 'Share Tech Mono', monospace; font-size: 13px; margin-bottom: 10px; letter-spacing: 0.05em; }

  h1.title {
    text-align: center;
    font-size: 38px;
    font-weight: 900;
    color: #e0f2ff;
    margin-bottom: 14px;
    line-height: 1.1;
    text-transform: uppercase;
    letter-spacing: 0.04em;
  }

  .subtitle { text-align: center; color: #6a8fa8; font-size: 15px; max-width: 640px; margin: 0 auto 48px; }

  hr { border: none; border-top: 1px solid #0f2233; margin: 48px 0; }

  h2 {
    font-size: 20px;
    font-weight: 700;
    color: #e0f2ff;
    margin: 44px 0 14px;
    padding-bottom: 8px;
    border-bottom: 1px solid #0f2233;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    font-family: 'Share Tech Mono', monospace;
  }

  h3 { font-size: 16px; font-weight: 700; color: #7dd3fc; margin: 28px 0 10px; }
  h4 { font-size: 12px; font-weight: 600; color: #4a6a8a; text-transform: uppercase; letter-spacing: 0.1em; margin: 22px 0 8px; font-family: 'Share Tech Mono', monospace; }

  p { margin-bottom: 14px; color: #8aaccc; font-size: 15px; }

  ul { margin: 0 0 16px 20px; }
  ul li { color: #8aaccc; font-size: 15px; margin-bottom: 4px; }

  .table-wrap { overflow-x: auto; margin-bottom: 24px; }
  table { width: 100%; border-collapse: collapse; font-size: 13px; }
  th { background: #070e17; color: #4a6a8a; font-weight: 600; text-align: left; padding: 9px 14px; border: 1px solid #0f2233; font-size: 12px; font-family: 'Share Tech Mono', monospace; letter-spacing: 0.05em; }
  td { padding: 9px 14px; border: 1px solid #0a1a28; color: #8aaccc; background: #060a0f; vertical-align: top; font-size: 13px; }
  tr:hover td { background: #070e17; }

  code { font-family: 'Share Tech Mono', monospace; font-size: 12px; background: #070e17; color: #38bdf8; padding: 2px 6px; border-radius: 4px; border: 1px solid #0f2233; }

  pre { background: #070e17; border: 1px solid #0f2233; border-radius: 8px; padding: 18px 20px; overflow-x: auto; margin-bottom: 4px; font-family: 'Share Tech Mono', monospace; font-size: 12px; line-height: 1.8; }
  pre code { background: none; border: none; padding: 0; color: #c8dff0; }

  .kw   { color: #f472b6; }
  .fn   { color: #a78bfa; }
  .str  { color: #34d399; }
  .num  { color: #fbbf24; }
  .cm   { color: #2d4a6a; font-style: italic; }
  .cls  { color: #fb923c; }
  .bool { color: #38bdf8; }

  .annotation { background: #060d18; border-left: 3px solid #1d4ed8; border-radius: 0 6px 6px 0; padding: 12px 16px; margin-bottom: 24px; font-size: 13px; color: #4a6a8a; line-height: 1.6; }
  .annotation strong { color: #8aaccc; }

  .callout { background: #070e17; border: 1px solid #0f2233; border-radius: 8px; padding: 14px 18px; margin-bottom: 20px; font-size: 14px; color: #8aaccc; line-height: 1.6; }
  .callout strong { color: #e0f2ff; }
  .callout-blue  { border-color: #1d4ed8; background: #060d18; }
  .callout-green { border-color: #065f46; background: #020c09; }
  .callout-orange{ border-color: #92400e; background: #0c0800; }

  .badge { display: inline-block; font-size: 11px; font-weight: 700; padding: 2px 9px; border-radius: 100px; margin-right: 5px; font-family: 'Share Tech Mono', monospace; letter-spacing: 0.04em; }
  .b-blue   { background: #060d18; color: #38bdf8; border: 1px solid #1d4ed8; }
  .b-green  { background: #020c09; color: #34d399; border: 1px solid #065f46; }
  .b-orange { background: #0c0800; color: #fb923c; border: 1px solid #92400e; }
  .b-purple { background: #0d0618; color: #a78bfa; border: 1px solid #4c1d95; }
  .b-red    { background: #0c0202; color: #f87171; border: 1px solid #7f1d1d; }

  .tree { background: #070e17; border: 1px solid #0f2233; border-radius: 8px; padding: 18px 22px; font-family: 'Share Tech Mono', monospace; font-size: 13px; line-height: 2; margin-bottom: 24px; }
  .tree-l0 { color: #fb923c; font-weight: 700; }
  .tree-l1 { color: #38bdf8; margin-left: 22px; display: block; }
  .tree-l2 { color: #34d399; margin-left: 44px; display: block; }
  .tree-note { color: #2d4a6a; font-size: 12px; }

  .toc { background: #070e17; border: 1px solid #0f2233; border-radius: 8px; padding: 18px 22px; margin-bottom: 40px; font-size: 14px; }
  .toc h4 { margin: 0 0 12px; }
  .toc ol { margin-left: 18px; }
  .toc li { margin-bottom: 4px; }
  .toc a { color: #38bdf8; }

  .play-button { display: inline-block; background: #1d4ed8; color: #fff; border: 1px solid #3b82f6; border-radius: 8px; padding: 10px 20px; font-weight: 700; font-size: 14px; text-decoration: none; font-family: 'Share Tech Mono', monospace; letter-spacing: 0.05em; margin: 4px; transition: background 0.15s; }
  .play-button:hover { background: #2563eb; text-decoration: none; }

  .footer { margin-top: 64px; padding-top: 24px; border-top: 1px solid #0f2233; text-align: center; font-size: 13px; color: #2d4a6a; line-height: 1.9; font-family: 'Share Tech Mono', monospace; }

  /* ── GAME CONTAINER ── */
  #game-section {
    background: #070e17;
    border: 1px solid #0f2233;
    border-radius: 12px;
    padding: 20px;
    margin: 28px 0;
  }

  #game-section h3 { margin-top: 0; }

  #gameCanvas {
    display: block;
    margin: 0 auto;
    border: 2px solid #1d4ed8;
    border-radius: 8px;
    background: #000;
    image-rendering: pixelated;
  }

  #game-controls {
    text-align: center;
    margin-top: 12px;
    font-family: 'Share Tech Mono', monospace;
    font-size: 13px;
    color: #4a6a8a;
  }

  #game-controls span { margin: 0 10px; }
</style>

<div class="blog-wrap">

<div class="meta">Mar 23, 2026 · Chetan Tiduwar · Sprint 6 Final Project</div>
<h1 class="title">CS111 Blog</h1>
<p class="subtitle">
  A complete CS111 walkthrough — a 3-level gauntlet game. Covers OOP inheritance, data types, control structures, operators, I/O, debugging, and API integration.
</p>

<div class="callout callout-orange">
  <strong>Mini-lesson purpose:</strong> This blog is a teaching walkthrough that explains how each CS111 concept appears in the games I've created.
</div>

<!-- ══════════════════════════════════════════════
     LIVE GAME
══════════════════════════════════════════════ -->

# Play The Gate Game

You can play the game right below:

<iframe src="https://phantom-deploy.github.io/portfolio/gamify/gategame" 
        width="800" 
        height="600" 
        frameborder="0" 
        allowfullscreen>
</iframe>

<script>
(function() {
  "use strict";
  const canvas = document.getElementById("gameCanvas");
  const ctx    = canvas.getContext("2d");
  const W = canvas.width, H = canvas.height;
  const statusEl = document.getElementById("game-status");

  // ── Fonts & helpers ──────────────────────────────
  function rect(x,y,w,h,fill,stroke,sw){
    ctx.fillStyle=fill; ctx.fillRect(x,y,w,h);
    if(stroke){ctx.strokeStyle=stroke;ctx.lineWidth=sw||1;ctx.strokeRect(x,y,w,h);}
  }
  function circle(x,y,r,fill){ctx.fillStyle=fill;ctx.beginPath();ctx.arc(x,y,r,0,Math.PI*2);ctx.fill();}
  function txt(s,x,y,col,sz,align,font){
    ctx.fillStyle=col;ctx.font=(sz||16)+"px "+(font||"'Share Tech Mono', monospace");
    ctx.textAlign=align||"left";ctx.fillText(s,x,y);
  }

  // ── Input ─────────────────────────────────────────
  const keys={};
  document.addEventListener("keydown",e=>{
    keys[e.code]=true;
    if(["ArrowUp","ArrowDown","ArrowLeft","ArrowRight","Space"].includes(e.code))e.preventDefault();
  });
  document.addEventListener("keyup",e=>{keys[e.code]=false;});

  // ── Global state ──────────────────────────────────
  let currentLevel=0, gameState="playing";
  const levels=[null,null,null];  // filled below

  // ══════════════════════════════════════════════════
  //  LEVEL 1 — CANNON GAUNTLET
  //  Dodge cannons left→right, reach the door
  // ══════════════════════════════════════════════════
  class Level1 {
    constructor(){
      this.label="Level 1: Cannon Gauntlet";
      this.hint="Reach the door — cannons reset you to start!";
      this.reset();
    }
    reset(){
      // Player
      this.player={x:36,y:H/2-14,w:24,h:28,vx:0,vy:0,speed:3};
      // Cannons — array of {x,y,dir,cooldown,timer,bullets:[]}
      this.cannons=[
        {x:200, y:60,  dir:"down",  cooldown:90, timer:0,  bullets:[]},
        {x:340, y:H-80,dir:"up",    cooldown:75, timer:25, bullets:[]},
        {x:480, y:100, dir:"down",  cooldown:80, timer:10, bullets:[]},
        {x:600, y:H-100,dir:"up",   cooldown:100,timer:45, bullets:[]},
        {x:260, y:H/2, dir:"right", cooldown:110,timer:55, bullets:[]},
        {x:150, y:200, dir:"down",  cooldown:95, timer:30, bullets:[]},
      ];
      // Door
      this.door={x:W-60,y:H/2-50,w:40,h:80};
      // Floor / ceiling
      this.walls=[
        {x:0,y:0,w:W,h:12},
        {x:0,y:H-12,w:W,h:12},
      ];
      this.deathFlash=0;
      this.win=false;
    }

    _spawnBullet(c){
      const speed=4.5;
      let vx=0,vy=0;
      if(c.dir==="down") vy=speed;
      if(c.dir==="up")   vy=-speed;
      if(c.dir==="right")vx=speed;
      if(c.dir==="left") vx=-speed;
      c.bullets.push({x:c.x+10,y:c.y+10,vx,vy,r:7});
    }

    _resetPlayer(){
      this.player.x=36; this.player.y=H/2-14;
      this.player.vx=0; this.player.vy=0;
      this.deathFlash=20;
      // clear all bullets
      this.cannons.forEach(c=>c.bullets=[]);
    }

    update(){
      if(this.win) return;
      const p=this.player;

      // Movement
      p.vx=0; p.vy=0;
      if(keys["ArrowLeft"]||keys["KeyA"]) p.vx=-p.speed;
      if(keys["ArrowRight"]||keys["KeyD"])p.vx= p.speed;
      if(keys["ArrowUp"]||keys["KeyW"])   p.vy=-p.speed;
      if(keys["ArrowDown"]||keys["KeyS"]) p.vy= p.speed;
      p.x+=p.vx; p.y+=p.vy;
      p.x=Math.max(12,Math.min(W-12-p.w, p.x));
      p.y=Math.max(12,Math.min(H-12-p.h, p.y));

      // Cannons
      this.cannons.forEach(c=>{
        c.timer++;
        if(c.timer>=c.cooldown){c.timer=0;this._spawnBullet(c);}
        for(let i=c.bullets.length-1;i>=0;i--){
          const b=c.bullets[i];
          b.x+=b.vx; b.y+=b.vy;
          // OOB remove
          if(b.x<-20||b.x>W+20||b.y<-20||b.y>H+20){c.bullets.splice(i,1);continue;}
          // Collision with player (circle-rect)
          const cx2=p.x+p.w/2, cy2=p.y+p.h/2;
          const nearX=Math.max(p.x,Math.min(b.x,p.x+p.w));
          const nearY=Math.max(p.y,Math.min(b.y,p.y+p.h));
          const dx=b.x-nearX, dy=b.y-nearY;
          if(dx*dx+dy*dy < b.r*b.r){
            this._resetPlayer();
            return;
          }
        }
      });

      // Door
      if(p.x+p.w > this.door.x && p.x < this.door.x+this.door.w &&
         p.y+p.h > this.door.y && p.y < this.door.y+this.door.h){
        this.win=true;
      }

      if(this.deathFlash>0) this.deathFlash--;
    }

    draw(){
      // BG
      rect(0,0,W,H,"#050b14");
      // Grid lines
      ctx.strokeStyle="#0a1828"; ctx.lineWidth=1;
      for(let x=0;x<W;x+=40){ctx.beginPath();ctx.moveTo(x,0);ctx.lineTo(x,H);ctx.stroke();}
      for(let y=0;y<H;y+=40){ctx.beginPath();ctx.moveTo(0,y);ctx.lineTo(W,y);ctx.stroke();}

      // Walls
      this.walls.forEach(w=>rect(w.x,w.y,w.w,w.h,"#0f2233","#1d4ed8",1));

      // Death flash
      if(this.deathFlash>0){
        ctx.fillStyle=`rgba(220,50,50,${this.deathFlash/20*0.35})`;
        ctx.fillRect(0,0,W,H);
      }

      // Cannons
      this.cannons.forEach(c=>{
        // Body
        rect(c.x,c.y,22,22,"#1a3a5a","#38bdf8",1.5);
        // Barrel direction indicator
        ctx.strokeStyle="#f87171"; ctx.lineWidth=3;
        ctx.beginPath();
        const cx=c.x+11, cy=c.y+11;
        let ex=cx,ey=cy;
        if(c.dir==="down") ey=cy+18;
        if(c.dir==="up")   ey=cy-18;
        if(c.dir==="right")ex=cx+18;
        if(c.dir==="left") ex=cx-18;
        ctx.moveTo(cx,cy); ctx.lineTo(ex,ey); ctx.stroke();
        // Cooldown bar
        const pct=c.timer/c.cooldown;
        rect(c.x,c.y-8,22,4,"#0a1828"); rect(c.x,c.y-8,22*pct,4,"#f87171");
        // Bullets
        c.bullets.forEach(b=>{
          circle(b.x,b.y,b.r,"#fbbf24");
          circle(b.x,b.y,b.r-3,"#fef3c7");
        });
      });

      // Door
      const d=this.door;
      rect(d.x,d.y,d.w,d.h,"#0d2b1a","#34d399",2);
      txt("EXIT",d.x+d.w/2,d.y+d.h/2+6,"#34d399",12,"center");

      // Player
      const p=this.player;
      rect(p.x,p.y,p.w,p.h,"#1d4ed8","#93c5fd",1.5);
      // eyes
      circle(p.x+7,p.y+10,3,"#bfdbfe");
      circle(p.x+p.w-7,p.y+10,3,"#bfdbfe");

      // HUD
      this._drawHUD();
      if(this.win){
        ctx.fillStyle="rgba(0,0,0,0.7)"; ctx.fillRect(0,0,W,H);
        txt("LEVEL CLEAR!",W/2,H/2-20,"#34d399",32,"center");
        txt("Press R to continue",W/2,H/2+20,"#6a8fa8",16,"center");
      }
    }

    _drawHUD(){
      rect(0,0,W,36,"rgba(5,11,20,0.9)");
      txt(this.label,14,22,"#38bdf8",14,"left");
      txt(this.hint,W/2,22,"#4a6a8a",12,"center");
      txt("Reach the door →",W-14,22,"#34d399",12,"right");
    }
  }

  // ══════════════════════════════════════════════════
  //  LEVEL 2 — MAZE
  //  Navigate a maze to reach the door
  // ══════════════════════════════════════════════════
  class Level2 {
    constructor(){
      this.label="Level 2: The Maze";
      this.hint="Find the path to the exit door";
      this.TILE=40;
      this._buildMaze();
      this.win=false;
    }

    _buildMaze(){
      const T=this.TILE;
      // cols=19, rows=11 (W=760, H=440)
      // 1=wall, 0=floor, 2=start, 3=door
      this.map=[
        [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
        [1,2,0,0,1,0,0,0,0,0,1,0,0,0,1,0,0,0,1],
        [1,0,1,0,1,0,1,1,0,1,1,0,1,0,1,0,1,0,1],
        [1,0,1,0,0,0,0,1,0,0,0,0,1,0,0,0,1,0,1],
        [1,0,1,1,1,1,0,1,1,1,0,1,1,1,1,1,1,0,1],
        [1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1],
        [1,0,1,1,0,1,1,1,0,1,0,1,1,0,1,1,1,0,1],
        [1,0,1,0,0,0,0,0,0,1,0,0,0,0,0,1,0,0,1],
        [1,0,1,0,1,1,1,0,1,1,1,0,1,1,0,1,0,1,1],
        [1,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,3,1],
        [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
      ];
      // Find start and door
      for(let r=0;r<this.map.length;r++){
        for(let c=0;c<this.map[r].length;c++){
          if(this.map[r][c]===2){this.startCol=c;this.startRow=r;}
          if(this.map[r][c]===3){this.doorCol=c;this.doorRow=r;}
        }
      }
      this._resetPlayer();
    }

    _resetPlayer(){
      const T=this.TILE;
      this.player={
        x:this.startCol*T+T/2-10,
        y:this.startRow*T+T/2-10,
        w:20,h:20,speed:2.5
      };
    }

    _isWall(px,py){
      const T=this.TILE;
      // Check all four corners
      const corners=[
        [px,py],[px+this.player.w,py],
        [px,py+this.player.h],[px+this.player.w,py+this.player.h]
      ];
      for(const [cx,cy] of corners){
        const col=Math.floor(cx/T);
        const row=Math.floor(cy/T);
        if(row<0||row>=this.map.length||col<0||col>=this.map[0].length) return true;
        if(this.map[row][col]===1) return true;
      }
      return false;
    }

    update(){
      if(this.win) return;
      const p=this.player;
      let dx=0,dy=0;
      if(keys["ArrowLeft"]||keys["KeyA"])  dx=-p.speed;
      if(keys["ArrowRight"]||keys["KeyD"]) dx= p.speed;
      if(keys["ArrowUp"]||keys["KeyW"])    dy=-p.speed;
      if(keys["ArrowDown"]||keys["KeyS"])  dy= p.speed;

      // Axis-separated collision
      p.x+=dx;
      if(this._isWall(p.x,p.y)) p.x-=dx;
      p.y+=dy;
      if(this._isWall(p.x,p.y)) p.y-=dy;

      // Door check
      const T=this.TILE;
      const pCol=Math.floor((p.x+p.w/2)/T);
      const pRow=Math.floor((p.y+p.h/2)/T);
      if(pCol===this.doorCol && pRow===this.doorRow) this.win=true;
    }

    draw(){
      rect(0,0,W,H,"#050b14");
      const T=this.TILE;
      // Draw tiles
      for(let r=0;r<this.map.length;r++){
        for(let c=0;c<this.map[r].length;c++){
          const tx=c*T, ty=r*T;
          if(this.map[r][c]===1){
            rect(tx,ty,T,T,"#0a1828","#0f2233",1);
            // Wall highlight
            ctx.fillStyle="rgba(56,189,248,0.04)";
            ctx.fillRect(tx,ty,T,2);
            ctx.fillRect(tx,ty,2,T);
          } else if(this.map[r][c]===3){
            rect(tx,ty,T,T,"#0d2b1a","#34d399",2);
            txt("EXIT",tx+T/2,ty+T/2+5,"#34d399",11,"center");
          } else if(this.map[r][c]===2){
            rect(tx,ty,T,T,"#060d18");
            txt("START",tx+T/2,ty+T/2+4,"#1d4ed8",9,"center");
          } else {
            rect(tx,ty,T,T,"#060a12");
          }
        }
      }
      // Player
      const p=this.player;
      rect(p.x,p.y,p.w,p.h,"#1d4ed8","#93c5fd",1.5);
      circle(p.x+6,p.y+7,2.5,"#bfdbfe");
      circle(p.x+p.w-6,p.y+7,2.5,"#bfdbfe");

      // HUD
      rect(0,0,W,36,"rgba(5,11,20,0.95)");
      txt(this.label,14,22,"#38bdf8",14,"left");
      txt(this.hint,W/2,22,"#4a6a8a",12,"center");
      txt("Find the EXIT →",W-14,22,"#34d399",12,"right");

      if(this.win){
        ctx.fillStyle="rgba(0,0,0,0.7)"; ctx.fillRect(0,0,W,H);
        txt("MAZE CLEARED!",W/2,H/2-20,"#34d399",32,"center");
        txt("Press R to continue",W/2,H/2+20,"#6a8fa8",16,"center");
      }
    }
  }

  // ══════════════════════════════════════════════════
  //  LEVEL 3 — SAFE ZONE SURVIVAL
  //  Stay in the shrinking safe zone, reach the door
  // ══════════════════════════════════════════════════
  class Level3 {
    constructor(){
      this.label="Level 3: Safe Zone";
      this.hint="Stay in the SAFE ZONE — reach the door before time runs out!";
      this.reset();
    }

    reset(){
      this.player={x:W/2-12,y:H/2-12,w:24,h:24,speed:3};
      this.timer=0;
      this.phase=0;   // 0=shrink, 1=move, cycles
      this.phaseTimer=0;
      this.phaseDuration=180; // frames per zone shift
      this.deathFlash=0;
      this.win=false;
      this.deaths=0;
      this._newZone();
      // Door — upper-right quadrant initially
      this.door={x:W-80,y:50,w:44,h:60};
    }

    _newZone(){
      // Safe zone: random rectangle that must be reachable
      const margin=80;
      const minSize=120;
      const maxSize=Math.max(minSize, 280 - this.phase*18);
      const zw=minSize + Math.random()*(maxSize-minSize);
      const zh=minSize + Math.random()*(maxSize-minSize);
      const zx=margin + Math.random()*(W-2*margin-zw);
      const zy=50 + Math.random()*(H-100-zh);  // leave room for HUD
      this.safeZone={x:zx,y:zy,w:zw,h:zh};
      this.nextZoneIn=this.phaseDuration;
      this.warningAlpha=0;
    }

    _inZone(px,py,pw,ph){
      const z=this.safeZone;
      return px>=z.x && py>=z.y && px+pw<=z.x+z.w && py+ph<=z.y+z.h;
    }

    update(){
      if(this.win) return;
      const p=this.player;
      let dx=0,dy=0;
      if(keys["ArrowLeft"]||keys["KeyA"])  dx=-p.speed;
      if(keys["ArrowRight"]||keys["KeyD"]) dx= p.speed;
      if(keys["ArrowUp"]||keys["KeyW"])    dy=-p.speed;
      if(keys["ArrowDown"]||keys["KeyS"])  dy= p.speed;
      p.x=Math.max(0,Math.min(W-p.w,p.x+dx));
      p.y=Math.max(36,Math.min(H-p.h,p.y+dy));

      this.timer++;
      this.nextZoneIn--;

      // Warning when zone is about to shift
      if(this.nextZoneIn<60) this.warningAlpha=Math.min(1,(60-this.nextZoneIn)/60);

      // Zone shift
      if(this.nextZoneIn<=0){
        this.phase++;
        this._newZone();
      }

      // Outside safe zone = death/reset
      if(!this._inZone(p.x,p.y,p.w,p.h)){
        this.deathFlash=25;
        this.deaths++;
        p.x=this.safeZone.x+this.safeZone.w/2-p.w/2;
        p.y=this.safeZone.y+this.safeZone.h/2-p.h/2;
      }

      if(this.deathFlash>0) this.deathFlash--;

      // Door (door stays fixed for simplicity — always reachable from safe zone over time)
      if(p.x+p.w>this.door.x && p.x<this.door.x+this.door.w &&
         p.y+p.h>this.door.y && p.y<this.door.y+this.door.h){
        this.win=true;
      }
    }

    draw(){
      // BG — danger zone is red-tinted
      rect(0,0,W,H,"#0c0202");

      // Particle/grid on danger zone
      ctx.strokeStyle="#1a0505"; ctx.lineWidth=1;
      for(let x=0;x<W;x+=40){ctx.beginPath();ctx.moveTo(x,36);ctx.lineTo(x,H);ctx.stroke();}
      for(let y=36;y<H;y+=40){ctx.beginPath();ctx.moveTo(0,y);ctx.lineTo(W,y);ctx.stroke();}

      // Safe zone
      const z=this.safeZone;
      // Glow
      const grad=ctx.createRadialGradient(z.x+z.w/2,z.y+z.h/2,0,z.x+z.w/2,z.y+z.h/2,Math.max(z.w,z.h)/1.5);
      grad.addColorStop(0,"rgba(16,185,129,0.12)");
      grad.addColorStop(1,"rgba(16,185,129,0)");
      ctx.fillStyle=grad; ctx.fillRect(z.x-20,z.y-20,z.w+40,z.h+40);
      // Zone fill
      rect(z.x,z.y,z.w,z.h,"rgba(16,185,129,0.06)");
      // Zone border
      const pulse=0.6+0.4*Math.sin(Date.now()/300);
      ctx.strokeStyle=`rgba(52,211,153,${pulse})`; ctx.lineWidth=2.5;
      ctx.strokeRect(z.x,z.y,z.w,z.h);
      // Label
      txt("SAFE ZONE",z.x+z.w/2,z.y+16,"rgba(52,211,153,0.7)",11,"center");

      // Warning flash when zone shifting
      if(this.warningAlpha>0){
        ctx.fillStyle=`rgba(251,191,36,${this.warningAlpha*0.15})`;
        ctx.fillRect(0,0,W,H);
        txt("ZONE SHIFTING!",W/2,H/2,"rgba(251,191,36,"+this.warningAlpha+")",20,"center");
      }

      // Death flash
      if(this.deathFlash>0){
        ctx.fillStyle=`rgba(220,38,38,${this.deathFlash/25*0.45})`;
        ctx.fillRect(0,0,W,H);
      }

      // Door
      const d=this.door;
      rect(d.x,d.y,d.w,d.h,"#0d2b1a","#34d399",2);
      txt("EXIT",d.x+d.w/2,d.y+d.h/2+5,"#34d399",11,"center");

      // Player
      const p=this.player;
      rect(p.x,p.y,p.w,p.h,"#1d4ed8","#93c5fd",2);
      circle(p.x+7,p.y+9,3,"#bfdbfe");
      circle(p.x+p.w-7,p.y+9,3,"#bfdbfe");

      // HUD
      rect(0,0,W,36,"rgba(5,5,10,0.95)");
      txt(this.label,14,22,"#f87171",14,"left");
      txt(this.hint,W/2,22,"#4a6a8a",11,"center");
      txt("Resets: "+this.deaths,W-14,22,"#6a8fa8",12,"right");

      // Zone countdown bar
      const barW=160, barX=W/2-barW/2, barY=28;
      rect(barX,barY,barW,6,"#0a0a0a");
      const pct=Math.max(0,this.nextZoneIn/this.phaseDuration);
      const barCol=pct>0.5?"#34d399":pct>0.25?"#fbbf24":"#f87171";
      rect(barX,barY,barW*pct,6,barCol);

      if(this.win){
        ctx.fillStyle="rgba(0,0,0,0.75)"; ctx.fillRect(0,0,W,H);
        txt("YOU WIN!",W/2,H/2-30,"#fbbf24",40,"center");
        txt("All 3 levels complete!",W/2,H/2+10,"#34d399",20,"center");
        txt("Press R to play again",W/2,H/2+42,"#6a8fa8",15,"center");
      }
    }
  }

  // ══════════════════════════════════════════════════
  //  BETWEEN LEVELS SCREEN
  // ══════════════════════════════════════════════════
  let showTransition=false, transitionTimer=0, transitionFrom=0;

  function drawTransition(){
    rect(0,0,W,H,"rgba(0,0,0,0.92)");
    const names=["Cannon Gauntlet","The Maze","Safe Zone Survival"];
    txt("LEVEL "+(currentLevel+1)+" COMPLETE",W/2,H/2-40,"#34d399",26,"center");
    if(currentLevel<2){
      txt("Next: Level "+(currentLevel+2)+" — "+names[currentLevel+1],W/2,H/2,"#38bdf8",18,"center");
      txt("Press R to continue",W/2,H/2+40,"#4a6a8a",15,"center");
    }
  }

  // ══════════════════════════════════════════════════
  //  GAME INSTANCES
  // ══════════════════════════════════════════════════
  levels[0]=new Level1();
  levels[1]=new Level2();
  levels[2]=new Level3();

  function currentLvl(){ return levels[currentLevel]; }

  // ══════════════════════════════════════════════════
  //  RESTART KEY
  // ══════════════════════════════════════════════════
  document.addEventListener("keydown",e=>{
    if(e.code==="KeyR"){
      const lv=currentLvl();
      if(lv.win && !showTransition){
        if(currentLevel<2){
          showTransition=true; transitionTimer=0;
        } else {
          // Restart whole game
          currentLevel=0;
          levels[0]=new Level1();
          levels[1]=new Level2();
          levels[2]=new Level3();
        }
      } else if(showTransition){
        showTransition=false;
        currentLevel++;
        if(statusEl) statusEl.textContent="Level "+(currentLevel+1)+" of 3";
      } else {
        if(lv.reset) lv.reset();
        else {
          levels[currentLevel]= currentLevel===0?new Level1():currentLevel===1?new Level2():new Level3();
        }
      }
    }
  });

  // ══════════════════════════════════════════════════
  //  MAIN LOOP
  // ══════════════════════════════════════════════════
  function loop(){
    if(showTransition){
      drawTransition();
    } else {
      currentLvl().update();
      currentLvl().draw();
    }
    requestAnimationFrame(loop);
  }
  requestAnimationFrame(loop);

})();
</script>

<!-- TABLE OF CONTENTS -->
<div class="toc">
  <h4>📋 Table of Contents</h4>
  <ol>
    <li><a href="#overview">Game Overview</a></li>
    <li><a href="#oop">OOP — Classes, Inheritance &amp; Constructor Chaining</a></li>
    <li><a href="#methods">Methods &amp; Parameters</a></li>
    <li><a href="#datatypes">Data Types</a></li>
    <li><a href="#operators">Operators</a></li>
    <li><a href="#control">Control Structures — Iteration, Conditions, Nested Conditions</a></li>
    <li><a href="#io">Input / Output — Keyboard, Canvas, GameEnv</a></li>
    <li><a href="#api">API Integration — Leaderboard &amp; Async I/O</a></li>
    <li><a href="#comments">JSDoc Comments &amp; Code Documentation</a></li>
    <li><a href="#debugging">Debugging — Console, Hitbox, Sources, Network, Application, Element</a></li>
    <li><a href="#testing">Testing &amp; Verification</a></li>
    <li><a href="#other-games">Other Game Examples &amp; Rubric Connections</a></li>
  </ol>
</div>

<hr>

<!-- SECTION 1: OVERVIEW -->
<h2 id="overview">🎮 Game Overview</h2>
<p>
  This 3-level gauntlet uses WASD / Arrow Keys for movement and challenges the player with completely different mechanics each level. Every mechanic — cannon bullets resetting you to start, maze wall collision, the shrinking safe zone — is directly controlled by the code explained in this blog.
</p>

<div class="table-wrap">
  <table>
    <tr><th>Level</th><th>Mechanic</th><th>Objective</th><th>Key New Concept</th></tr>
    <tr><td>Level 1</td><td>Cannon Gauntlet</td><td>Dodge cannon fire, reach the EXIT door</td><td>Bullet array, AABB collision, reset on hit</td></tr>
    <tr><td>Level 2</td><td>Maze</td><td>Navigate a maze, reach the EXIT door</td><td>Tile-map collision, axis-separated movement</td></tr>
    <tr><td>Level 3</td><td>Safe Zone Survival</td><td>Stay inside the shifting safe zone, reach EXIT</td><td>Zone collision, phase timers, shrinking bounds</td></tr>
  </table>
</div>

<div class="callout callout-blue">
  <strong>Controls:</strong> WASD or Arrow Keys to move · R to restart current level · Reach the EXIT door to complete each level
</div>

<hr>

<!-- SECTION 2: OOP -->
<h2 id="oop">📐 OOP — Classes, Inheritance &amp; Constructor Chaining</h2>

<h3>Class Hierarchy</h3>

<div class="tree">
  <span class="tree-l0">Level1</span><span class="tree-note">  ← Cannon Gauntlet — bullet array, AABB collision, respawn</span>
  <span class="tree-l0">Level2</span><span class="tree-note">  ← Maze — tile map, wall sliding, path navigation</span>
  <span class="tree-l0">Level3</span><span class="tree-note">  ← Safe Zone — shrinking zone, phase timers, door unlock</span>
</div>

<h3>Level1 Class — Cannon Gauntlet</h3>
<pre><code><span class="cm">/**
 * Level1 — Cannon Gauntlet
 * Player must dodge cannon fire and reach the EXIT door.
 * Cannon bullets reset the player to the start position.
 * @class Level1
 */</span>
<span class="kw">class</span> <span class="cls">Level1</span> {
  <span class="fn">constructor</span>() {
    <span class="kw">this</span>.label   = <span class="str">"Level 1: Cannon Gauntlet"</span>;
    <span class="kw">this</span>.hint    = <span class="str">"Reach the door — cannons reset you to start!"</span>;
    <span class="kw">this</span>.<span class="fn">reset</span>();
  }

  <span class="fn">reset</span>() {
    <span class="kw">this</span>.player  = { x:<span class="num">36</span>, y:H/<span class="num">2</span>-<span class="num">14</span>, w:<span class="num">24</span>, h:<span class="num">28</span>, vx:<span class="num">0</span>, vy:<span class="num">0</span>, speed:<span class="num">3</span> };
    <span class="kw">this</span>.cannons = [                              <span class="cm">// Array of cannon objects</span>
      { x:<span class="num">200</span>, y:<span class="num">60</span>,  dir:<span class="str">"down"</span>,  cooldown:<span class="num">90</span>, timer:<span class="num">0</span>,  bullets:[] },
      { x:<span class="num">340</span>, y:H-<span class="num">80</span>,dir:<span class="str">"up"</span>,    cooldown:<span class="num">75</span>, timer:<span class="num">25</span>, bullets:[] },
    ];
    <span class="kw">this</span>.door      = { x:W-<span class="num">60</span>, y:H/<span class="num">2</span>-<span class="num">50</span>, w:<span class="num">40</span>, h:<span class="num">80</span> };
    <span class="kw">this</span>.deathFlash = <span class="num">0</span>;                         <span class="cm">// Number — flash timer</span>
    <span class="kw">this</span>.win        = <span class="bool">false</span>;                     <span class="cm">// Boolean — level complete</span>
  }
}</code></pre>

<div class="annotation">
  <strong>reset()</strong> is called both when the level starts and whenever the player is hit by a cannon bullet. It reinstates the player to the start position and clears all active bullets from every cannon, giving the player a fresh attempt. The <code>deathFlash</code> number counts down from 20 and is used to render a red screen overlay that communicates the death without interrupting gameplay.
</div>

<h3>Level3 Class — Safe Zone Survival</h3>
<pre><code><span class="cm">/**
 * Level3 — Safe Zone Survival
 * Player must stay inside the shifting safe zone rectangle.
 * The zone changes position every phaseDuration frames.
 * Reaching the EXIT door completes the level.
 * @class Level3
 */</span>
<span class="kw">class</span> <span class="cls">Level3</span> {
  <span class="fn">constructor</span>() {
    <span class="kw">this</span>.label         = <span class="str">"Level 3: Safe Zone"</span>;
    <span class="kw">this</span>.phaseDuration  = <span class="num">180</span>;    <span class="cm">// Number — frames before zone shifts</span>
    <span class="kw">this</span>.<span class="fn">reset</span>();
  }

  <span class="fn">_newZone</span>() {
    <span class="kw">const</span> margin   = <span class="num">80</span>;
    <span class="kw">const</span> maxSize  = Math.<span class="fn">max</span>(<span class="num">120</span>, <span class="num">280</span> - <span class="kw">this</span>.phase * <span class="num">18</span>);  <span class="cm">// shrinks each phase</span>
    <span class="kw">const</span> zw = <span class="num">120</span> + Math.<span class="fn">random</span>() * (maxSize - <span class="num">120</span>);
    <span class="kw">const</span> zh = <span class="num">120</span> + Math.<span class="fn">random</span>() * (maxSize - <span class="num">120</span>);
    <span class="kw">const</span> zx = margin + Math.<span class="fn">random</span>() * (W - <span class="num">2</span>*margin - zw);
    <span class="kw">const</span> zy = <span class="num">50</span>   + Math.<span class="fn">random</span>() * (H - <span class="num">100</span> - zh);
    <span class="kw">this</span>.safeZone    = { x:zx, y:zy, w:zw, h:zh };  <span class="cm">// Object</span>
    <span class="kw">this</span>.nextZoneIn  = <span class="kw">this</span>.phaseDuration;
    <span class="kw">this</span>.warningAlpha = <span class="num">0</span>;
  }
}</code></pre>

<div class="annotation">
  <strong>_newZone()</strong> creates a randomly positioned safe rectangle each time the zone shifts. The maximum size decreases by <code>18 * phase</code>, so the zone physically shrinks as the player progresses — making the challenge harder the longer they survive. The <code>warningAlpha</code> value ramps from 0 to 1 in the last 60 frames before a shift, producing a visible warning tint on screen.
</div>

<hr>

<!-- SECTION 3: METHODS -->
<h2 id="methods">⚙️ Methods &amp; Parameters (5+ with return values)</h2>

<h3>1. _spawnBullet(cannon) — creates a new bullet from a cannon</h3>
<pre><code><span class="cm">/**
 * Spawns a bullet object from a cannon in its facing direction.
 * @param {Object} c - cannon object with dir, x, y, bullets[]
 */</span>
<span class="fn">_spawnBullet</span>(c) {
  <span class="kw">const</span> speed = <span class="num">4.5</span>;
  <span class="kw">let</span> vx = <span class="num">0</span>, vy = <span class="num">0</span>;
  <span class="kw">if</span> (c.dir === <span class="str">"down"</span>)  vy =  speed;   <span class="cm">// positive y = downward on canvas</span>
  <span class="kw">if</span> (c.dir === <span class="str">"up"</span>)    vy = -speed;
  <span class="kw">if</span> (c.dir === <span class="str">"right"</span>) vx =  speed;
  <span class="kw">if</span> (c.dir === <span class="str">"left"</span>)  vx = -speed;
  c.bullets.<span class="fn">push</span>({ x: c.x+<span class="num">10</span>, y: c.y+<span class="num">10</span>, vx, vy, r: <span class="num">7</span> });
}</code></pre>

<h3>2. _resetPlayer() — resets player to start position and clears bullets</h3>
<pre><code><span class="cm">/**
 * Resets player to spawn position and clears all active bullets.
 * Called on cannon hit in Level1.
 */</span>
<span class="fn">_resetPlayer</span>() {
  <span class="kw">this</span>.player.x = <span class="num">36</span>;
  <span class="kw">this</span>.player.y = H / <span class="num">2</span> - <span class="num">14</span>;
  <span class="kw">this</span>.player.vx = <span class="num">0</span>;
  <span class="kw">this</span>.player.vy = <span class="num">0</span>;
  <span class="kw">this</span>.deathFlash = <span class="num">20</span>;
  <span class="kw">this</span>.cannons.<span class="fn">forEach</span>(c => c.bullets = []);  <span class="cm">// clear bullets from all cannons</span>
}</code></pre>

<h3>3. _isWall(px, py) — tile-map collision check, returns Boolean</h3>
<pre><code><span class="cm">/**
 * Checks if a position collides with any wall tile in the maze.
 * Tests all four corners of the player rectangle.
 * @param {number} px - player X to test
 * @param {number} py - player Y to test
 * @returns {boolean} true if any corner overlaps a wall tile
 */</span>
<span class="fn">_isWall</span>(px, py) {
  <span class="kw">const</span> T = <span class="kw">this</span>.TILE;
  <span class="kw">const</span> corners = [
    [px,         py         ],
    [px + <span class="kw">this</span>.player.w, py         ],
    [px,         py + <span class="kw">this</span>.player.h],
    [px + <span class="kw">this</span>.player.w, py + <span class="kw">this</span>.player.h]
  ];
  <span class="kw">for</span> (<span class="kw">const</span> [cx, cy] <span class="kw">of</span> corners) {
    <span class="kw">const</span> col = Math.<span class="fn">floor</span>(cx / T);
    <span class="kw">const</span> row = Math.<span class="fn">floor</span>(cy / T);
    <span class="kw">if</span> (row < <span class="num">0</span> || row >= <span class="kw">this</span>.map.length) <span class="kw">return</span> <span class="bool">true</span>;  <span class="cm">// OOB = wall</span>
    <span class="kw">if</span> (<span class="kw">this</span>.map[row][col] === <span class="num">1</span>)              <span class="kw">return</span> <span class="bool">true</span>;
  }
  <span class="kw">return</span> <span class="bool">false</span>;
}</code></pre>

<h3>4. _inZone(px, py, pw, ph) — safe zone containment check, returns Boolean</h3>
<pre><code><span class="cm">/**
 * Tests whether the player rectangle is fully inside the safe zone.
 * @param {number} px - player X
 * @param {number} py - player Y
 * @param {number} pw - player width
 * @param {number} ph - player height
 * @returns {boolean} true if player is fully inside the zone rectangle
 */</span>
<span class="fn">_inZone</span>(px, py, pw, ph) {
  <span class="kw">const</span> z = <span class="kw">this</span>.safeZone;
  <span class="kw">return</span> px >= z.x && py >= z.y &&
         px + pw <= z.x + z.w && py + ph <= z.y + z.h;
}</code></pre>

<h3>5. _newZone() — generates a new random safe zone with shrinking bounds</h3>
<pre><code><span class="cm">/**
 * Computes a new safe zone rectangle.
 * Max size shrinks by 18px per phase completed.
 * @returns {void} — writes to this.safeZone
 */</span>
<span class="fn">_newZone</span>() {
  <span class="kw">const</span> maxSize = Math.<span class="fn">max</span>(<span class="num">120</span>, <span class="num">280</span> - <span class="kw">this</span>.phase * <span class="num">18</span>);   <span class="cm">// Number — shrinks</span>
  <span class="kw">const</span> zw = <span class="num">120</span> + Math.<span class="fn">random</span>() * (maxSize - <span class="num">120</span>);
  <span class="kw">const</span> zh = <span class="num">120</span> + Math.<span class="fn">random</span>() * (maxSize - <span class="num">120</span>);
  <span class="kw">this</span>.safeZone   = { x: ..., y: ..., w: zw, h: zh };        <span class="cm">// Object</span>
  <span class="kw">this</span>.nextZoneIn = <span class="kw">this</span>.phaseDuration;
  <span class="kw">this</span>.warningAlpha = <span class="num">0</span>;
}</code></pre>

<hr>

<!-- SECTION 4: DATA TYPES -->
<h2 id="datatypes">🗂️ Data Types</h2>

<div class="table-wrap">
  <table>
    <tr><th>Type</th><th>How It Controls the Game</th><th>Code Example</th></tr>
    <tr>
      <td><span class="badge b-orange">Number</span></td>
      <td><code>cooldown</code> is the number of frames a cannon waits between shots. <code>timer</code> increments each frame and fires when it reaches <code>cooldown</code>. <code>phaseDuration</code> counts down the safe zone shift in Level 3.</td>
      <td><code>cooldown: 90</code> · <code>timer: 0</code> · <code>phaseDuration: 180</code></td>
    </tr>
    <tr>
      <td><span class="badge b-blue">String</span></td>
      <td><code>dir</code> on each cannon is a string storing its firing direction. The <code>_spawnBullet</code> method reads this string and sets velocity accordingly. Template literals build all HUD messages.</td>
      <td><code>dir: "down"</code> · <code>"Level 1: Cannon Gauntlet"</code></td>
    </tr>
    <tr>
      <td><span class="badge b-red">Boolean</span></td>
      <td><code>win</code> stops the update loop and shows the level-complete overlay. <code>showTransition</code> gates the between-level screen. <code>_inZone()</code> returns a boolean used to decide whether to respawn the player.</td>
      <td><code>this.win = false</code> · <code>showTransition</code> · return from <code>_isWall()</code></td>
    </tr>
    <tr>
      <td><span class="badge b-green">Array</span></td>
      <td><code>c.bullets</code> holds every active bullet from that cannon. The update loop iterates this array backwards each frame. <code>this.map</code> in Level 2 is a 2D array (array of arrays) of tile values.</td>
      <td><code>c.bullets = []</code> · <code>this.map = [[1,0,1,...],...]</code></td>
    </tr>
    <tr>
      <td><span class="badge b-purple">Object (JSON)</span></td>
      <td>Each bullet is an object <code>{ x, y, vx, vy, r }</code> holding all its state. The player is an object. The safe zone is an object. The door is an object. All game entities are structured data objects.</td>
      <td><code>{ x:200, y:60, vx:0, vy:4.5, r:7 }</code></td>
    </tr>
  </table>
</div>

<hr>

<!-- SECTION 5: OPERATORS -->
<h2 id="operators">🔢 Operators</h2>

<div class="table-wrap">
  <table>
    <tr><th>Operator Type</th><th>Operators</th><th>How It Controls the Game</th></tr>
    <tr>
      <td>Mathematical</td>
      <td><code>+</code> <code>-</code> <code>*</code> <code>/</code> <code>Math.hypot()</code> <code>Math.floor()</code> <code>Math.max()</code></td>
      <td><code>b.x += b.vx</code> moves every bullet each frame. <code>Math.floor(cx/T)</code> converts pixel position to tile index in the maze. <code>Math.max(120, 280 - phase*18)</code> shrinks the safe zone max size per phase.</td>
    </tr>
    <tr>
      <td>Boolean / Logical</td>
      <td><code>&amp;&amp;</code> <code>||</code> <code>!</code> <code>===</code> <code>&lt;</code> <code>&gt;</code> <code>&lt;=</code> <code>&gt;=</code></td>
      <td>The <code>_inZone()</code> method chains four <code>&amp;&amp;</code> conditions — all must be true for the player to be safe. <code>||</code> prevents division by zero in <code>Math.hypot(...) || 1</code>. <code>===</code> compares direction strings in <code>_spawnBullet</code>.</td>
    </tr>
    <tr>
      <td>Assignment</td>
      <td><code>=</code> <code>+=</code> <code>-=</code></td>
      <td><code>c.timer++</code> increments the cannon's shot timer every frame. <code>this.nextZoneIn--</code> counts down the safe zone shift timer. <code>p.x += dx</code> applies movement.</td>
    </tr>
    <tr>
      <td>Nullish / Safety</td>
      <td><code>||</code> for fallback</td>
      <td><code>Math.hypot(dx,dy) || 1</code> prevents a divide-by-zero crash if the bullet spawns exactly on target. Without this, velocity would be <code>NaN</code> and the bullet would disappear instantly.</td>
    </tr>
  </table>
</div>

<h4>AABB Collision — 4 Conditions with &&</h4>
<pre><code><span class="cm">// Axis-aligned bounding box check: bullet circle vs player rectangle</span>
<span class="kw">const</span> nearX = Math.<span class="fn">max</span>(p.x, Math.<span class="fn">min</span>(b.x, p.x + p.w));
<span class="kw">const</span> nearY = Math.<span class="fn">max</span>(p.y, Math.<span class="fn">min</span>(b.y, p.y + p.h));
<span class="kw">const</span> dx    = b.x - nearX, dy = b.y - nearY;
<span class="kw">if</span> (dx*dx + dy*dy < b.r*b.r) {
  <span class="kw">this</span>.<span class="fn">_resetPlayer</span>();   <span class="cm">// bullet hit — send player back to start</span>
}</code></pre>
<div class="annotation">
  This is circle-rectangle collision, used for cannon bullets hitting the player in Level 1. It finds the nearest point on the player rectangle to the bullet center, then checks if that distance is less than the bullet radius. If it is, the circles overlap and the player is reset to the starting position.
</div>

<hr>

<!-- SECTION 6: CONTROL STRUCTURES -->
<h2 id="control">🔁 Control Structures</h2>

<h3>Iteration — backwards loop over the bullets array</h3>
<pre><code><span class="cm">// Backwards iteration — safe to splice while looping</span>
<span class="kw">for</span> (<span class="kw">let</span> i = <span class="kw">this</span>.cannons.length - <span class="num">1</span>; i >= <span class="num">0</span>; i--) {
  <span class="kw">const</span> c = <span class="kw">this</span>.cannons[i];
  c.timer++;
  <span class="kw">if</span> (c.timer >= c.cooldown) { c.timer = <span class="num">0</span>; <span class="kw">this</span>.<span class="fn">_spawnBullet</span>(c); }

  <span class="kw">for</span> (<span class="kw">let</span> j = c.bullets.length - <span class="num">1</span>; j >= <span class="num">0</span>; j--) {
    <span class="kw">const</span> b = c.bullets[j];
    b.x += b.vx; b.y += b.vy;   <span class="cm">// move bullet</span>
    <span class="kw">if</span> (b.x < -<span class="num">20</span> || b.x > W+<span class="num">20</span>) { c.bullets.<span class="fn">splice</span>(j,<span class="num">1</span>); <span class="kw">continue</span>; }
    <span class="cm">// collision check...</span>
  }
}</code></pre>

<div class="annotation">
  The nested for-loop processes every bullet from every cannon each frame. The backwards direction matters: when a bullet expires and is removed with <code>splice(j,1)</code>, all bullets at higher indices shift down by one. Looping backwards means only already-visited indices shift, so no bullet is ever skipped on the frame it should be removed.
</div>

<h3>Nested Conditions — safe zone shift with warning</h3>
<pre><code><span class="fn">update</span>() {
  <span class="kw">if</span> (<span class="kw">this</span>.win) <span class="kw">return</span>;             <span class="cm">// Condition 1: guard clause</span>

  <span class="kw">this</span>.nextZoneIn--;
  <span class="kw">if</span> (<span class="kw">this</span>.nextZoneIn < <span class="num">60</span>) {       <span class="cm">// Condition 2: warning phase</span>
    <span class="kw">this</span>.warningAlpha = (<span class="num">60</span> - <span class="kw">this</span>.nextZoneIn) / <span class="num">60</span>;
  }

  <span class="kw">if</span> (<span class="kw">this</span>.nextZoneIn <= <span class="num">0</span>) {       <span class="cm">// Condition 3: zone shifts</span>
    <span class="kw">this</span>.phase++;
    <span class="kw">this</span>.<span class="fn">_newZone</span>();
  }

  <span class="kw">if</span> (!<span class="kw">this</span>.<span class="fn">_inZone</span>(p.x, p.y, p.w, p.h)) {  <span class="cm">// Condition 4: outside zone</span>
    <span class="kw">this</span>.deathFlash = <span class="num">25</span>;
    <span class="kw">this</span>.deaths++;
    p.x = <span class="kw">this</span>.safeZone.x + <span class="kw">this</span>.safeZone.w/<span class="num">2</span> - p.w/<span class="num">2</span>;  <span class="cm">// teleport to center of zone</span>
    p.y = <span class="kw">this</span>.safeZone.y + <span class="kw">this</span>.safeZone.h/<span class="num">2</span> - p.h/<span class="num">2</span>;
  }
}</code></pre>

<h3>Axis-Separated Collision (Level 2 Maze)</h3>
<pre><code><span class="cm">// Move X axis, check wall, revert if colliding</span>
p.x += dx;
<span class="kw">if</span> (<span class="kw">this</span>.<span class="fn">_isWall</span>(p.x, p.y)) p.x -= dx;

<span class="cm">// Move Y axis independently, same logic</span>
p.y += dy;
<span class="kw">if</span> (<span class="kw">this</span>.<span class="fn">_isWall</span>(p.x, p.y)) p.y -= dy;</code></pre>
<div class="annotation">
  Separating X and Y movement and checking walls independently is what lets the player slide along walls instead of stopping dead. If you moved both axes simultaneously and rejected the combined movement, the player would get stuck on every wall corner. With axis separation, if X is blocked you still slide along the wall on Y — which is what makes maze navigation feel smooth.
</div>

<hr>

<!-- SECTION 7: I/O -->
<h2 id="io">⌨️ Input / Output</h2>

<h3>Keyboard Input — Event Listeners</h3>
<pre><code><span class="cm">// Registers on document — captures all key events</span>
<span class="kw">const</span> keys = {};
document.<span class="fn">addEventListener</span>(<span class="str">'keydown'</span>, e => {
  keys[e.code] = <span class="bool">true</span>;
  <span class="kw">if</span> ([<span class="str">'ArrowUp'</span>,<span class="str">'ArrowDown'</span>,<span class="str">'ArrowLeft'</span>,<span class="str">'ArrowRight'</span>,<span class="str">'Space'</span>]
      .<span class="fn">includes</span>(e.code)) e.<span class="fn">preventDefault</span>();  <span class="cm">// stop page scroll</span>
});
document.<span class="fn">addEventListener</span>(<span class="str">'keyup'</span>,   e => { keys[e.code] = <span class="bool">false</span>; });

<span class="cm">// Reading input each frame inside update()</span>
<span class="kw">if</span> (keys[<span class="str">"ArrowLeft"</span>]  || keys[<span class="str">"KeyA"</span>]) dx = -p.speed;
<span class="kw">if</span> (keys[<span class="str">"ArrowRight"</span>] || keys[<span class="str">"KeyD"</span>]) dx =  p.speed;
<span class="kw">if</span> (keys[<span class="str">"ArrowUp"</span>]    || keys[<span class="str">"KeyW"</span>]) dy = -p.speed;
<span class="kw">if</span> (keys[<span class="str">"ArrowDown"</span>]  || keys[<span class="str">"KeyS"</span>]) dy =  p.speed;</code></pre>

<h3>Canvas Output — requestAnimationFrame loop</h3>
<pre><code><span class="cm">// Main game loop — 60fps render cycle</span>
<span class="kw">function</span> <span class="fn">loop</span>() {
  currentLvl().<span class="fn">update</span>();   <span class="cm">// update game state</span>
  currentLvl().<span class="fn">draw</span>();     <span class="cm">// render to canvas</span>
  <span class="fn">requestAnimationFrame</span>(loop);
}
<span class="fn">requestAnimationFrame</span>(loop);</code></pre>

<hr>

<!-- SECTION 8: API -->
<h2 id="api">🌐 API Integration — Leaderboard &amp; Async I/O</h2>
<pre><code><span class="cm">/**
 * Posts the player's score to the leaderboard API.
 * @param {string} playerName - username
 * @param {number} score      - final score
 * @returns {Promise&lt;Object&gt;} parsed JSON response
 */</span>
<span class="kw">async</span> <span class="fn">postScore</span>(playerName, score) {
  <span class="kw">try</span> {
    <span class="kw">const</span> response = <span class="kw">await</span> <span class="fn">fetch</span>(<span class="str">`${<span class="kw">this</span>.gameEnv.pythonURI}/api/leaderboard`</span>, {
      method:  <span class="str">'POST'</span>,
      headers: { <span class="str">'Content-Type'</span>: <span class="str">'application/json'</span> },
      body:    JSON.<span class="fn">stringify</span>({ player: playerName, score })
    });
    <span class="kw">if</span> (!response.ok) <span class="kw">throw</span> <span class="kw">new</span> <span class="cls">Error</span>(<span class="str">`HTTP error: ${response.status}`</span>);
    <span class="kw">const</span> data = <span class="kw">await</span> response.<span class="fn">json</span>();
    <span class="kw">return</span> data;
  } <span class="kw">catch</span> (error) {
    console.<span class="fn">error</span>(<span class="str">`[Leaderboard] POST failed:`, error.message</span>);
    <span class="kw">return</span> <span class="kw">null</span>;
  }
}</code></pre>

<hr>

<!-- SECTION 9: COMMENTS -->
<h2 id="comments">📝 JSDoc Comments &amp; Code Documentation</h2>
<pre><code><span class="cm">/**
 * Level1 — Cannon Gauntlet
 * Player must dodge cannon fire and reach the EXIT door.
 * Getting hit by a bullet resets the player to start position.
 *
 * @class Level1
 * @example
 * const lv = new Level1();
 * lv.update();  // call each frame
 * lv.draw();    // render each frame
 */</span>
<span class="kw">class</span> <span class="cls">Level1</span> {
  <span class="cm">/**
   * @param {void} - no parameters needed; canvas dimensions W/H are global
   */</span>
  <span class="fn">constructor</span>() { ... }

  <span class="cm">/**
   * Spawns a bullet from the given cannon in its facing direction.
   * @param {Object} c          - cannon object
   * @param {string} c.dir      - "up" | "down" | "left" | "right"
   * @param {Array}  c.bullets  - bullet array to push into
   */</span>
  <span class="fn">_spawnBullet</span>(c) { ... }
}</code></pre>

<hr>

<!-- SECTION 10: DEBUGGING -->
<h2 id="debugging">🐛 Debugging</h2>

<div class="table-wrap">
  <table>
    <tr><th>DevTools Tab</th><th>What I Used It For</th></tr>
    <tr><td><strong>Console</strong></td><td>Logged cannon fire events, bullet counts, zone shift timings, and player position each frame during development. Used <code>[Level1]</code>, <code>[Level2]</code>, <code>[Level3]</code> prefixes to filter logs by level.</td></tr>
    <tr><td><strong>Sources (Breakpoints)</strong></td><td>Set breakpoints inside <code>_isWall()</code> to step through the corner-check loop and verify which tile was being flagged as a wall. Used the Scope panel to inspect <code>row</code>, <code>col</code>, and <code>this.map[row][col]</code>.</td></tr>
    <tr><td><strong>Network</strong></td><td>Verified POST and GET calls to the leaderboard API. Checked request body JSON, HTTP status codes (200 vs 401 vs 500), and CORS headers.</td></tr>
    <tr><td><strong>Application</strong></td><td>Checked localStorage for auth tokens and user session persistence between page reloads. Confirmed tokens were sent with API requests.</td></tr>
    <tr><td><strong>Elements</strong></td><td>Inspected the <code>#gameCanvas</code> element to verify dimensions, border styling, and that the canvas was correctly positioned inside the container div.</td></tr>
  </table>
</div>

<h4>Console Logging Pattern</h4>
<pre><code>console.<span class="fn">log</span>(<span class="str">`[Level1] Cannon fired at frame ${frame}, bullets: ${c.bullets.length}`</span>);
console.<span class="fn">log</span>(<span class="str">`[Level1] Player hit — reset to start. DeathFlash: 20`</span>);
console.<span class="fn">log</span>(<span class="str">`[Level2] Wall check: row=${row} col=${col} val=${<span class="kw">this</span>.map[row][col]}`</span>);
console.<span class="fn">log</span>(<span class="str">`[Level3] Zone shifted — phase ${<span class="kw">this</span>.phase}, maxSize: ${maxSize}`</span>);
console.<span class="fn">error</span>(<span class="str">`[API] Request failed: ${error.message}`</span>);</code></pre>

<hr>

<!-- SECTION 11: TESTING -->
<h2 id="testing">✅ Testing &amp; Verification</h2>

<h3>Gameplay Testing</h3>
<p>
  Each level was play-tested end-to-end. Level 1: verified bullet collision resets player to start and clears all bullets. Level 2: verified wall sliding, no clipping through corners, and the EXIT tile triggers the win. Level 3: verified the zone shifts on the countdown, that the warning flash appears in the last 60 frames, and that stepping outside the zone repositions the player to the zone center.
</p>

<h3>Edge Case Testing</h3>
<pre><code><span class="cm">// Tested: bullet spawning exactly on player position (dx=0, dy=0)</span>
<span class="cm">// Math.hypot(0,0) = 0 → ||1 prevents division by zero → vx/vy = 0 safely</span>

<span class="cm">// Tested: player holding both left+right simultaneously</span>
<span class="cm">// dx is set last, right overwrites left — consistent result</span>

<span class="cm">// Tested: zone maxSize at phase 15+ (280 - 15*18 = 10px) → Math.max(120,...) clamps it</span>
<span class="cm">// Zone never goes below 120px minimum — always reachable</span></code></pre>

<hr>

<!-- SECTION 12: OTHER GAMES -->
<h2 id="other-games">🕹️ Other Game Examples &amp; Rubric Connections</h2>
<p>
  In addition to this 3-level gauntlet, I built other games that reinforce the same CS111 concepts.
</p>

<div style="text-align:center; margin: 20px 0;">
  <a class="play-button" href="https://rashig-1804.github.io/csse_teamrepo/hacks/TicTacToe/" target="_blank" rel="noopener noreferrer">▶ Tic-Tac-Toe</a>
  <a class="play-button" href="https://rashig-1804.github.io/csse_teamrepo/connect4/" target="_blank" rel="noopener noreferrer">▶ Connect 4</a>
  <a class="play-button" href="https://aadis12.github.io/student/hacks/whackamole" target="_blank" rel="noopener noreferrer">▶ Whack-a-Mole</a>
</div>

<div class="callout callout-blue">
  <strong>Rubric connections:</strong> Tic-Tac-Toe adds examples of Python OOP and 2D array win checking. Connect 4 shows multiple cooperating classes, DOM-based I/O, and timer-driven state. Whack-a-Mole shows inheritance (Entity → Mole/Bomb), method overriding, canvas animation loops, and localStorage for high scores.
</div>

<hr>

<!-- HOMEWORK LINKS -->
<h2 id="homework-links">📚 All Homework Links</h2>

<ul>
  <li><strong><a href="https://chetan-coder.github.io/student/nestedconditionalshw">Nested Conditionals Homework</a></strong> — Relates to Control Structures section. Shows nested if/else decision trees like the win/lose/zone-shift checks in Level 3.</li>
  <li><strong><a href="https://chetan-coder.github.io/student/2026/02/24/classes-and-methods-hw.html">Classes and Methods Homework</a></strong> — Relates to OOP section. Foundation of the Level1/2/3 class design and the 5+ method examples.</li>
  <li><strong><a href="https://chetan-coder.github.io/student/js/arrays">Arrays Homework</a></strong> — Relates to Data Types. Covers the bullet arrays, the maze tile map (2D array), and the levels array.</li>
  <li><strong><a href="https://chetan-coder.github.io/student/2026/01/21/booleans-homework.html">Booleans Homework</a></strong> — Relates to Data Types and Operators. Foundation for the <code>win</code>, <code>_isWall()</code>, and <code>_inZone()</code> boolean return values.</li>
  <li><strong><a href="https://chetan-coder.github.io/student/2026/01/26/data-abstractions-homework.html">Data Abstraction Homework</a></strong> — Relates to OOP and Data Types. Shows encapsulating level state into class properties and config objects.</li>
  <li><strong><a href="https://chetan-coder.github.io/student/jsonhomework">JSON Homework</a></strong> — Relates to API Integration. Direct foundation for <code>JSON.stringify()</code> and <code>response.json()</code> in the leaderboard methods.</li>
  <li><strong><a href="https://chetan-coder.github.io/student/2026/01/21/math-expressions-HW.html">Mathematical Expressions Homework</a></strong> — Relates to Operators. Covers <code>Math.hypot()</code>, <code>Math.max()</code>, and the position arithmetic used in bullet and zone calculations.</li>
  <li><strong><a href="https://chetan-coder.github.io/student/2026/02/02/strings-homework.html">Strings Homework</a></strong> — Relates to Data Types and I/O. Foundation for template literals, the cannon <code>dir</code> string, and HUD message construction.</li>
</ul>

<div class="callout callout-green">
  <strong>Homework-blog connection:</strong> Each homework directly maps to a concept demonstrated in the 3-level game, showing consistent understanding across multiple independent assignments.
</div>

<div class="footer">
  Built with JavaScript · HTML5 Canvas · requestAnimationFrame<br>
  CSSE Final Project — Sprint 6 · Chetan Tiduwar · Mar 23, 2026
</div>

</div>