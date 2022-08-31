<script>
  import { onMount } from "svelte";

  let canvas;

  onMount(() => {
    const ctx = canvas.getContext("2d");

    let draw = (x, y, c, s) => {
      ctx.fileStyle = c;
      ctx.fillRect(x, y, s, s);
    };

    let particles = [];
    let particle = (x, y, c) => {
      return { "x": x, "y": y, "vx": 0, "vy": 0, "color": c };
    };

    let random = () => {
      return Math.random() * 400 + 50;
    };

    let create = (number, color) => {
      let group = [];
      for (let i = 0; i < number; i++) {
        group.push(particle(random(), random(), color));
        particles.push(group[i]);
      }
      return group;
    };

    create(200, "yellow");

    let update = () => {
      ctx.clearRect(0, 0, 500, 500);
      draw(0, 0, "black", 500);
      for (let i = 0; i < particles.length; i++) {
        draw(particles[i].x, particles[i].y, particles[i].color, 5);
      }
      requestAnimationFrame(update);
    };

    update();
  });
</script>

<div id="clusters">

  <canvas
    bind:this={canvas}
  ></canvas>
</div>

<style>
    #clusters {
        width: 100%;
        height: 100%;
    }

    canvas {
        width: 500px;
        height: 500px;
        background-color: #666;
    }
</style>