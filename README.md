# jQueryRockScissorsPaperGame
Rock Scissors Paper Game using jQuery

<img src="./srp/srp.png" width="100px">


<!DOCTYPE html>
<html>

<head>
  <title>jQuery Rock Scissors Paper Game</title>
  <style>
    .box1 {
      border-radius: 10px;
      border: 2px solid #73ad21;
      background-color: #73ad21;
      padding: 10px;
      margin: 10px;
      width: 400px;
      height: 20px;
      color: white;
      text-align: center;
    }

    .box2 {
      width: 400px;
      height: 200px;
      background-color: greenyellow;
      /* margin-top: 10px; */
      margin-left: 10px;
      padding: 10px;
      text-align: center;
      border: 2px solid grey;
      float: left;
    }

    #bt1 {
      background-color: greenyellow;
      border-radius: 5px;
      padding: 5px;
    }

    #msgimg {
      width: 420px;
      margin-top: 225px;
      margin-left: 10px;
      padding-top: 10px;
      height: 160px;
      border: 2px solid black;
      background-color: rgb(0, 183, 255);
      text-align: center;
      float: both clear;
    }

    #txt1,
    #txt2 {
      display: inline-block;
      border-radius: 5px;
      background-color: chocolate;
      border: 2px solid brown;
    }

    #txt1 {
      margin-left: 80px;
      margin-right: 50px;

    }

    #txt2 {
      margin-right: 50px;
      margin-left: 100px;
    }

    #msg {
      background-color: rgb(10, 125, 163);
      padding-top: 20px;
      margin-top: 0px;
      margin-left: 10px;
      width: 420px;
      height: 80px;
      border: 2px solid black;
      text-align: center;
    }
  </style>
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
  <script>
    var clickCnt = 0;
    var winCnt = 0;
    $(document).ready(function () {
      $('#i1,#i2, #i3').click(function () {
        clickCnt++;
        // take out the number that's clicked on one of the SRP(scissors,rock, paper)
        var n = parseInt($(this).attr('id').charAt(1));

        // generate a random number among 1 and 3 (S=1, R=2, P=3)
        var com = Math.floor(Math.random() * 3) + 1;
        /* put a corresponding picture using jQuery and replacing src attribute
        in id = img1, img2 */

        $('#img1').attr('src', './SRP/' + n + '.png');
        $('#img2').attr('src', './SRP/c' + com + '.png');

        /* if the one user click win over the one generated randomly, 
        show "you win", if even, show "you are even", otherwise, show "you lose".
        count the total trial number and the number you win and % win
        */
        var str = '';
        if ((n == 1 && com == 3) || (n == 2 && com == 1) || (n == 3 && com == 1)) {
          str = str + 'You win !' + '<br>';
          winCnt++;
        } else if (n == com) {
          str = str + 'You are even !' + '<br>';
        } else {
          str = str + 'You lose !' + '<br>';
        }

        str = str + 'Number of Trial: ' + clickCnt + ',  ';
        str = str + 'Win Number: ' + winCnt + "(";
        str = str + (winCnt / clickCnt * 100) + '%' + ')';
        $('#msg').html(str);
      });
      /*  redo will reset the dice chosen by user and randomly selected 
      and the statement(you got wrong or you got wrong) and the score  
      */
      $('input[type=button]').click(function () {
        $('#img1').attr('src', './SRP/q.png');
        $('#img2').attr('src', './SRP/q.png');
        $('#msg').html('');
        clickCnt = 0;
        winCnt = 0;
      });
    });
  </script>
</head>

<body>
  <form name="form1">
    <div class="box1">jQuery Rock Scisors Paper Game</div>
    <div class="box2">
      <p>
        <img width="100" src="./SRP/1.png" id="i1">
        <img width="100" src="./SRP/2.png" id="i2">
        <img width="100" src="./SRP/3.png" id="i3">
      </p>

      <p>
        <input type="button" value="Redo" id="bt1" />
      </p>
    </div>
    <div id="msgimg">
      <img width="100" src="./SRP/q.png" id="img1" />
      <img width="100" src="./SRP/vs.png" />
      <img width="100" src="./SRP/q.png" id="img2" />
      <p id="txt1">
        YOU
      </p>
      <p id="txt2">
        COMPUTER
      </p>
    </div>

    <div id="msg"></div>
  </form>
</body>

</html>
