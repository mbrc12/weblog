---
title: "First"
date: 2023-07-11T06:42:52+05:30
draft: true
---
Lets check math $\eta_{\mu\nu}$

\begin{align}
    \Pr(X > \mu) & \leq \frac{\mathbf{E} X}{\mu}
\end{align}

`Inline code` is also as expected.

```ts
import { BG_COLOR, HEIGHT, WIDTH } from './globals';
// import Main from './scenes/main';

import { Game, WEBGL } from 'phaser';
// import ECSTest from './scenes/ecstest';
import { PauseScene } from './scenes/pause';
import { InitScene } from './scenes/init';
import MainGame from './scenes/game';
import { NinePatchPlugin } from '@koreez/phaser3-ninepatch';
import { GameOverScene } from './scenes/game-over';
// import TiledTest from './scenes/tiled-test';


///////////////// GAME SETUP ////////////////////////

const canvas = document.getElementById('game') as HTMLCanvasElement;

const computeZoom = (w: number, h: number, tw: number, th: number) => Math.min(tw/w, th/h);

const config = {
    type: WEBGL,
    width: WIDTH,
    height: HEIGHT,
    backgroundColor: BG_COLOR,
    autoCenter: Phaser.Scale.CENTER_VERTICALLY,
    zoom: computeZoom(WIDTH, HEIGHT, window.innerWidth, window.innerHeight),
    canvas,
    scene: [
        // TiledTest
        InitScene,
        MainGame,
        PauseScene,
        GameOverScene
    ],
    // antialias: false,
    pixelArt: true,
    autoFocus: true,
    disableContextMenu: true,

    fps: {
        target: 60,
        forceSetTimeOut: true
    },
    plugins: {
        global: [{ key: 'NinePatchPlugin', plugin: NinePatchPlugin, start: true }],
    },

    // pipeline: { name: 'ShaderFX', pipeline: ShaderFX },
}

const game = new Game(config);

//// resize event handler

window.addEventListener("resize", () => {
    const zoom = computeZoom(WIDTH, HEIGHT, window.innerWidth, window.innerHeight);
    game.scale.setZoom(zoom);
});
```


