# Akash-s-Tic-Tac-Toe
Wanna time pass? Play this one!! A game made by using htm, css and js only...
<!DOCTYPE html>

<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Tic Tac Toe</title>

    <link rel="stylesheet" href="style.css">

</head>

<body>

    <div class="container">

        <h1>Akash's Tic Tac Toe</h1>

        <div class="board">

            <div class="cell" id="cell0" onclick="makeMove(0)"></div>

            <div class="cell" id="cell1" onclick="makeMove(1)"></div>

            <div class="cell" id="cell2" onclick="makeMove(2)"></div>

            <div class="cell" id="cell3" onclick="makeMove(3)"></div>



            <div class="cell" id="cell4" onclick="makeMove(4)"></div>

            <div class="cell" id="cell5" onclick="makeMove(5)"></div>

            <div class="cell" id="cell6" onclick="makeMove(6)"></div>

            <div class="cell" id="cell7" onclick="makeMove(7)"></div>

            <div class="cell" id="cell8" onclick="makeMove(8)"></div>

        </div>

        <button onclick="resetGame()">Play another match !</button>

        <p id="status"></p>

    </div>

    <script src="script.js"></script>

</body>

</html>

<style>body {



    font-family: Arial, sans-serif;

    display: flex;

    justify-content: center;

    align-items: center;

    height: 100vh;

    margin: 0;

    background-color: #f4f4f4;

}



.container {

    text-align: center;

}



.board {

    display: grid;

    grid-template-columns: repeat(3, 100px);

    grid-template-rows: repeat(3, 100px);

    gap: 5px;

    margin-bottom: 20px;

}



.cell {



    width: 100px;

    height: 100px;

    display: flex;

    justify-content: center;

    align-items: center;

    font-size: 2em;

    background-color: #fff;

    border: 1px solid #333;

    cursor: pointer;

}



button {

    padding: 10px 20px;

    font-size: 1em;

    cursor: pointer;

}



#status {

    margin-top: 20px;

    font-size: 1.2em;

}

</style><script>let board = ['', '', '', '', '', '', '', '', ''];

let currentPlayer = 'You';

let gameActive = true;

const statusDisplay = document.querySelector('#status');



const winningConditions = [

    [0, 1, 2],

    [3, 4, 5],

    [6, 7, 8],

    [0, 3, 6],

    [1, 4, 7],

    [2, 5, 8],

    [0, 4, 8],

    [2, 4, 6]

];



function handleResultValidation() {

    let roundWon = false;

    for (let i = 0; i < 8; i++) {

        const winCondition = 



winningConditions[i];

        let a = board[winCondition[0]];

        let b = board[winCondition[1]];

        let c = board[winCondition[2]];

        if (a === '' || b === '' || c === '') {

            continue;

        }

        if (a === b && b === c) {

            roundWon = true;

            break;

        }

    }



    if (roundWon) {

        statusDisplay.innerHTML = `${currentPlayer} win! Congratulations from Akash.`;

        gameActive = false;

        return;

    }



    let roundDraw = !board.includes('');

    if (roundDraw) {



        statusDisplay.innerHTML = `It's a draw!`;

        gameActive = false;

        return;

    }



    currentPlayer = currentPlayer === 'You' ? 'Comp.' : 'You';

}



function makeMove(index) {

    if (board[index] !== '' || !gameActive) {

        return;

    }



    board[index] = currentPlayer;

    document.getElementById(`cell${index}`).innerHTML = currentPlayer;

    handleResultValidation();



    if (gameActive && currentPlayer === 'Comp.') {

        computerMove();

    }

}



function computerMove() {

    let availableCells = board.map((val, index) => val === '' ? index : null).filter(val => val !== null);

    let randomIndex = availableCells[Math.floor(Math.random() * availableCells.length)];

    makeMove(randomIndex);

}



function resetGame() {

    board = ['', '', '', '', '', '', '', '', ''];

    currentPlayer = 'You';

    gameActive = true;

    document.querySelectorAll('.cell').forEach(cell => cell.innerHTML = '');

    statusDisplay.innerHTML = '';

}






</script>
