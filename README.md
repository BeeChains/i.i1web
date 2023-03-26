# i.i1web
Handshake site on .i1web TLD at [reg.uncensorednames/](https://reg.uncensorednames.com/)
<html>
<head>
<title>Cyber Matrix Roots</title>
<style>
 body {
 background-color: black;
       }
		
 canvas {
 display: block;
 position: fixed;
 top: 0;
 left: 0;
 z-index: -1;
       }
</style>
</head>
<body>
<canvas id="matrix"></canvas>
	
<script>
    const canvas = document.getElementById('matrix');
    const context = canvas.getContext('2d');

    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const columnWidth = 20;
    const columns = Math.floor(canvas.width / columnWidth);

    const goldenRatio = 1.61803398875;

    function generateRoots() {
        const roots = [];
        const numRoots = Math.floor(Math.random() * 10) + 5; // Generate random number of roots
        let a = 1, b = 1;
        for (let i = 0; i < numRoots; i++) {
            roots.push(Math.floor(a));
            const temp = b;
            b = a;
            a += temp * goldenRatio;
        }
        return roots;
    }

    function draw() {
        context.fillStyle = '#000';
        context.fillRect(0, 0, canvas.width, canvas.height);

        for (let i = 0; i < columns; i++) {
            const x = i * columnWidth + columnWidth / 2;
            const roots = generateRoots();
            let y = canvas.height;
            for (let j = 0; j < roots.length; j++) {
                const noise = Math.random() * 5 - 2.5;
                const hue = Math.random() * 360;
                context.fillStyle = `hsl(${hue}, 100%, 50%)`;
                context.fillText(roots[j], x, y + noise);
                y -= columnWidth;
            }
        }
    }

    setInterval(draw, 100);

</script>
</body>
</html>
