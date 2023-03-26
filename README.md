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

    const columnWidth = 10;
    const columns = Math.floor(canvas.width / columnWidth);

    const goldenRatio = 1.61803398875;
    const rootLength = Math.floor(canvas.height / columnWidth);
    const roots = generateRoots(rootLength, goldenRatio);

    function generateRoots(length, ratio) {
        const roots = [];
        let a = 1, b = 1;
        for (let i = 0; i < length; i++) {
            roots.push(Math.floor(a));
            const temp = b;
            b = a;
            a += temp * ratio;
        }
        return roots;
    }

    function draw() {
        context.fillStyle = 'rgba(0, 0, 0, 0.05)';
        context.fillRect(0, 0, canvas.width, canvas.height);

        context.fillStyle = '#0F0';
        context.font = '15px monospace';

        for (let i = 0; i < columns; i++) {
            const x = i * columnWidth;
            let y = canvas.height;
            for (let j = roots.length - 1; j >= 0; j--) {
                context.fillText(roots[j], x, y);
                y -= columnWidth;
            }
            roots.unshift(roots.pop());
        }
    }

    setInterval(draw, 33);
</script>
</body>
</html>
