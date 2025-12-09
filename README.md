<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Mobile Tetris Game - Single File</title>
    
    <style>
        :root {
            --board-width: 10;
            --board-height: 20;
            --cell-size: 25px; /* 모바일에서 보기 좋게 조정 */
        }

        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            background-color: #1a1a2e;
            color: white;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            padding: 10px;
            margin: 0;
            touch-action: manipulation;
            overflow: hidden;
        }

        #game-info {
            display: flex;
            justify-content: center;
            align-items: center;
            width: calc(var(--board-width) * var(--cell-size));
            margin-bottom: 10px;
            font-size: 1.2em;
        }

        #game-board {
            display: grid;
            grid-template-columns: repeat(var(--board-width), var(--cell-size));
            grid-template-rows: repeat(var(--board-height), var(--cell-size));
            border: 5px solid #000;
            background-color: #333;
            box-shadow: 0 0 20px rgba(0, 255, 255, 0.5);
        }

        .grid-cell {
            width: var(--cell-size);
            height: var(--cell-size);
            box-sizing: border-box;
            border: 1px solid #555;
            transition: background-color 0.1s ease-out;
        }

        /* 테트로미노 색상 정의 */
        .T { background-color: #800080; border-color: #a020a0; }
        .O { background-color: #ffff00; border-color: #ffd700; }
        .J { background-color: #0000ff; border-color: #1e90ff; }
        .L { background-color: #ffa500; border-color: #ff8c00; }
        .I { background-color: #00ffff; border-color: #00ced1; }
        .S { background-color: #008000; border-color: #3cb371; }
        .Z { background-color: #ff0000; border-color: #dc143c; }
        .filled { border: 2px solid #000; }

        /* 모바일 컨트롤 버튼 스타일 */
        #controls {
            display: flex;
            justify-content: space-around;
            align-items: center;
            width: 100%;
            max-width: calc(var(--board-width) * var(--cell-size) + 50px);
            padding: 20px 0;
            margin-top: 15px;
        }

        #controls button {
            padding: 15px 10px;
            font-size: 1.1em;
            font-weight: bold;
            cursor: pointer;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 8px;
            flex-grow: 1;
            margin: 0 5px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
            transition: background-color 0.2s, transform 0.1s;
        }

        #controls button:active {
            background-color: #218838;
            transform: translateY(2px);
        }

        #game-message {
            margin-top: 20px;
            font-size: 1.5em;
            font-weight: bold;
            color: #ffd700;
            text-shadow: 0 0 10px rgba(255, 215, 0, 0.7);
            text-align: center;
        }
    </style>
</head>
<body>
    
    <div id="game-info">
        <h3>점수: <span id="score">0</span></h3>
    </div>
    <div id="game-board">
        </div>
