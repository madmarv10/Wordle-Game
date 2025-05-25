const wordList = [
  "PLANE", "CODES", "BREAD", "LEAFY", "STARE",
  "ZEBRA", "NOTES", "QUIRK", "SHEEP", "NIGHT"
];

let currentRound = 0;
let targetWord = wordList[currentRound];
let currentRow = 0;
const maxTries = 6;

const board = document.getElementById("game-board");
const guessInput = document.getElementById("guess-input");
const submitBtn = document.getElementById("submit-btn");
const roundInfo = document.getElementById("round-info");
const message = document.getElementById("message");

submitBtn.addEventListener("click", submitGuess);

function submitGuess() {
  const guess = guessInput.value.toUpperCase().trim();
  if (guess.length !== 5) {
    showMessage("Please enter a 5-letter word.");
    return;
  }

  if (currentRow >= maxTries) {
    showMessage("No more guesses! Click Submit to go to next round.");
    return;
  }

  createRow(guess);
  currentRow++;

  if (guess === targetWord) {
    showMessage("🎉 Correct! Moving to next round...");
    nextRound(true);
  } else if (currentRow === maxTries) {
    showMessage(`❌ Out of tries! The word was: ${targetWord}`);
    nextRound(false);
  } else {
    guessInput.value = "";
  }
}

function createRow(guess) {
  for (let i = 0; i < 5; i++) {
    const tile = document.createElement("div");
    tile.classList.add("tile");

    const letter = guess[i];
    tile.textContent = letter;

    if (letter === targetWord[i]) {
      tile.classList.add("correct");
    } else if (targetWord.includes(letter)) {
      tile.classList.add("present");
    } else {
      tile.classList.add("absent");
    }

    board.appendChild(tile);
  }
}

function nextRound(correctGuess) {
  setTimeout(() => {
    currentRound++;
    if (currentRound >= wordList.length) {
      showMessage("🎮 Game over! All 10 rounds complete.");
      submitBtn.disabled = true;
      guessInput.disabled = true;
      return;
    }

    // Reset
    targetWord = wordList[currentRound];
    currentRow = 0;
    board.innerHTML = "";
    guessInput.value = "";
    showMessage("");
    roundInfo.textContent = `Round ${currentRound + 1} of ${wordList.length}`;
  }, correctGuess ? 1500 : 2500);
}

function showMessage(msg) {
  message.textContent = msg;
}
