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

	const columns = Math.floor(canvas.width / 10);

	const drops = [];
	for (let i = 0; i < columns; i++) {
		drops[i] = Math.floor(Math.random() * canvas.height);
	}

	function draw() {
		context.fillStyle = 'rgba(0, 0, 0, 0.05)';
		context.fillRect(0, 0, canvas.width, canvas.height);
		
		context.fillStyle = '#0F0';
		context.font = '15px monospace';
		
		for (let i = 0; i < drops.length; i++) {
			const text = String.fromCharCode(Math.floor(Math.random() * 128));
			context.fillText(text, i * 10, drops[i]);
			
			if (drops[i] * 10 > canvas.height && Math.random() > 0.95) {
				drops[i] = 0;
			}
			
			drops[i]++;
		}
	}

	setInterval(draw, 33);
</script>
</body>
</html>
