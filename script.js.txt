let seconds = 30;
let timer;

function startTimer() {
    timer = setInterval(function() {
        document.getElementById('timer').innerText = seconds;
        seconds--;

        if (seconds < 0) {
            clearInterval(timer);
            submitFeedback();
        }
    }, 1000);
}

function submitFeedback() {
    clearInterval(timer);

    const textFeedback = document.getElementById('textFeedback').value;
    const selectedFruit = document.querySelector('input[name="fruit"]:checked');
    const fruitCount = document.getElementById('fruitCount').value;

    let result = `Text Feedback: ${textFeedback}\n`;
    result += `Favorite Fruit: ${selectedFruit ? selectedFruit.value : 'Not answered'}\n`;
    result += `Fruits Eaten per Day: ${fruitCount || 'Not answered'}`;

    document.getElementById('result').innerText = result;
}
