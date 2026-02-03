---
layout: post
codemirror: true
title: Game Runner Examples
description: Learn game development using the GameEngine framework in a contained educational environment. Build game levels, add characters, and create interactive experiences with live code editing and debugging controls.
permalink: /rpg/game

---

## Basic Game: Desert Adventure - RPG Game

{% capture challenge1 %}
Run the basic desert adventure game. Use WASD or arrow keys to move Chill Guy around the desert. Walk up to R2D2 to trigger a mini-game!
{% endcapture %}

{% capture code1 %}
import GameEnvBackground from '/assets/js/BetterGameEngine/essentials/GameEnvBackground.js';
import Player from '/assets/js/BetterGameEngine/gameObjects/Player.js';
import Npc from '/assets/js/BetterGameEngine/gameObjects/Npc.js';
import Barrier from '/assets/js/adventureGame/Barrier.js';

class CustomLevel {
            constructor(gameEnv) {
            const path = gameEnv.path;
            const width = gameEnv.innerWidth;
            const height = gameEnv.innerHeight;
        const bgData = {
            name: 'custom_bg',
            src: path + "/images/gamebuilder/alien_planet.jpg",
            pixels: { height: 600, width: 1000 }
        };
        const playerData = {
            id: 'Bob',
            src: path + "/images/gamify/chillguy.png",
            SCALE_FACTOR: 5,
            STEP_FACTOR: 1000,
            ANIMATION_RATE: 50,
            INIT_POSITION: { x: 100, y: 300 },
            pixels: { height: 512, width: 384 },
            orientation: { rows: 4, columns: 3 },
            down: { row: 0, start: 0, columns: 3 },
            downRight: { row: Math.min(1, 4 - 1), start: 0, columns: 3, rotate: Math.PI/16 },
            downLeft: { row: Math.min(2, 4 - 1), start: 0, columns: 3, rotate: -Math.PI/16 },
            right: { row: Math.min(1, 4 - 1), start: 0, columns: 3 },
            left: { row: Math.min(2, 4 - 1), start: 0, columns: 3 },
            up: { row: Math.min(3, 4 - 1), start: 0, columns: 3 },
            upRight: { row: Math.min(1, 4 - 1), start: 0, columns: 3, rotate: -Math.PI/16 },
            upLeft: { row: Math.min(2, 4 - 1), start: 0, columns: 3, rotate: Math.PI/16 },
            hitbox: { widthPercentage: 0.45, heightPercentage: 0.2 },
            keypress: { up: 87, left: 65, down: 83, right: 68 }
        };
        const npcData1 = {
            id: 'NPC',
            greeting: 'Yo wassup!',
            src: path + "/images/gamify/chillguy.png",
            SCALE_FACTOR: 8,
            ANIMATION_RATE: 50,
            INIT_POSITION: { x: 500, y: 300 },
            pixels: { height: 512, width: 384 },
            orientation: { rows: 4, columns: 3 },
            down: { row: 0, start: 0, columns: 3 },
            hitbox: { widthPercentage: 0.1, heightPercentage: 0.2 },
            dialogues: ['Yo wassup!'],
            reaction: function() { if (this.dialogueSystem) { this.showReactionDialogue(); } else { console.log(this.greeting); } },
            interact: function() { if (this.dialogueSystem) { this.showRandomDialogue(); } }
        };

        this.classes = [
                  { class: GameEnvBackground, data: bgData },
      { class: Player, data: playerData },
      { class: Npc, data: npcData1 }
        ];
    }
}

export const gameLevelClasses = [CustomLevel];
{% endcapture %}

{% include game-runner.html
   runner_id="game1"
   challenge=challenge1
   code=code1
   height="150px"
%}
