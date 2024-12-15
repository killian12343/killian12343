<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Changewear Online Shop</title>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            overflow: hidden;
            background-color: #000;
        }

        #intro {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            background: url('porsche.jpg') no-repeat center center/cover;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: all 1s ease-in-out;
            opacity: 1;
            z-index: 2;
        }

        #intro.laferrari {
            background: url('laferrari.jpg') no-repeat center center/cover;
        }

        #shop {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            background-color: #fff;
            display: flex;
            justify-content: center;
            align-items: center;
            opacity: 0;
            z-index: 1;
            transform: scale(0.9);
            transition: all 1s ease-in-out;
        }

        #shop.open {
            opacity: 1;
            z-index: 3;
            transform: scale(1);
        }

        .door {
            position: absolute;
            top: 0;
            width: 50%;
            height: 100%;
            background: #000;
            transition: transform 1s ease-in-out;
            z-index: 3;
        }

        .door.left {
            left: 0;
            transform: translateX(0);
        }

        .door.right {
            right: 0;
            transform: translateX(0);
        }

        .door.open.left {
            transform: translateX(-100%);
        }

        .door.open.right {
            transform: translateX(100%);
        }

        .shop-content {
            text-align: center;
            color: #333;
        }

        .shop-content h1 {
            font-size: 3rem;
        }

        .shop-content p {
            font-size: 1.2rem;
            color: #555;
        }

        .enter-button {
            position: absolute;
            bottom: 50px;
            background-color: #fff;
            color: #000;
            padding: 15px 30px;
            font-size: 1.2rem;
            border: none;
            cursor: pointer;
            z-index: 4;
        }
    </style>
</head>
<body>
    <div id="intro">
        <button class="enter-button">Enter Shop</button>
    </div>

    <div id="shop">
        <div class="door left"></div>
        <div class="door right"></div>
        <div class="shop-content">
            <h1>Welcome to Changewear</h1>
            <p>Change it. Explore our unique fashion collection.</p>
        </div>
    </div>

    <script>
        const intro = document.getElementById('intro');
        const shop = document.getElementById('shop');
        const enterButton = document.querySelector('.enter-button');
        const doors = document.querySelectorAll('.door');

        let carSwitch = true;
        setInterval(() => {
            if (carSwitch) {
                intro.classList.add('laferrari');
            } else {
                intro.classList.remove('laferrari');
            }
            carSwitch = !carSwitch;
        }, 3000);

        enterButton.addEventListener('click', () => {
            intro.style.opacity = '0';
            setTimeout(() => {
                intro.style.zIndex = '0';
                shop.classList.add('open');
                doors.forEach(door => door.classList.add('open'));
            }, 1000);
        });
    </script>
</body>
</html>

