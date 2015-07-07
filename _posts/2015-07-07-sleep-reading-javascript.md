---
layout: post
title: "Sleep, Reading, and JavaScript"
date: 2015-07-07
categories: technical omahacodeschool javascript
---

In an attempt to not go completely insane with stress from school + life + procrastination + etc., I have been abstaining from watching TV, reading, and going to bed before midnight nearly every night. It's been quite a departure from my normal behavior for the past few years. I feel good, though. I don't think I have watched TV since 6/23, and I haven't really missed it.

Switching gears, I am not a huge fan of CSS. JavaScript, I am in love with for the moment. More updates to come later.

```html
<!doctype html>
  <html>
    <head>
      <title>Quiz Game</title>
      <script type="text/javascript" src="global.js"></script>
    </head>

    <body>

    </body>

  </html>
  ```

  ```javascript
  //Questions
  var q1 = {question: ("Arrays in Ruby can contain values of which type?"), options: "1: Integers, 2: Characters, 3: Strings, 4: Any type", answer: "4"};
  var q2 = {question: ("What is the difference between a Hash and an Array in Ruby?"), options: "1: Hashes can have a non-integer index, 2: The size of a hash is not fixed, 3: There is no difference, 4: None of these", answer: "1"};
  var q3 = {question: ("Which of the following is a primitive type in Ruby?"), options: "1: Integer, 2: String, 3: Float, 4: None of these", answer: "4"};
  var q4 = {question: ("A __________ takes your source code, converts it into machine language, and stores it in an executable file."), options: "1: Program, 2: Compiler, 3: Debugger, 4: Text editor", answer: "2"};
  var q5 = {question: ("__________ is writing step-by-step instructions telling the computer exactly what you want it to do."), options: "1: Designing, 2: Scripting, 3: Programming, 4: Encoding", answer: "3"};

  //Score
  var questions = [q1, q2, q3, q4, q5];
  var correct = 0;

  for (var i = 0; i < questions.length; i++) {
    alert(questions[i].question);
    var input = prompt(questions[i].options);
    console.log("User input = " + input);
    console.log("Correct answer = " + questions[i].answer);
    if (input === questions[i].answer) {
      alert("Correct!");
      correct++;
    }
    else {
      alert("Incorrect!")
    }
  }
  console.log("# correct: " + correct);
  console.log("# questions: " + questions.length);

  var score = 100 * (correct/questions.length)
  console.log("Your score is " + score + "%");
  ```
