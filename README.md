# FCC-Quotes-Machine
Diff color Quotes Machine use in HTML CSS JAVASCRIPT Frontend development used this project
<!-- 
💻💻💻HTML CODE💻💻💻(❁´◡`❁)</>
Hello Camper!

Please read the README below in the JS Editor before beginning. Feel free to delete this message once you have read it. Good luck and Happy Coding! 

- The freeCodeCamp Team 

-->
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" href="styles.css" />
    <link
      rel="stylesheet"
      href="https://maxcdn.bootstrapcdn.com/font-awesome/4.3.0/css/font-awesome.min.css"
    />
    <title>FCC : Random "Quote Machine"</title>
  </head>
  <body>
    <div id="wrapper">
      <div id="quote-box">
        <div class="quote-text">
          <i class="fa fa-quote-left"> </i><span id="text"></span>
        </div>
        <div class="quote-author">- <span id="author"></span></div>
        <div class="buttons">
          <a
            class="button"
            id="tweet-quote"
            title="Tweet this quote!"
            target="_top"
          >
            <i class="fa fa-twitter"></i>
          </a>
          <a
            class="button"
            id="tumblr-quote"
            title="Post this quote on tumblr!"
            target="_blank"
          >
            <i class="fa fa-tumblr"></i>
          </a>
          <button class="button" id="new-quote">New quote</button>
        </div>
      </div>
      <div class="footer">by <a href="https://codepen.io/AbhiCoder08/">AbhiCoder08</a></div>
    </div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.2/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jqueryui/1.13.2/jquery-ui.min.js"></script>
    <script src="script.js"></script>
  </body>
</html>


💻💻💻CSS CODE💻💻💻→$$§§{};

@import url('https://fonts.googleapis.com/css?family=Raleway:400,500');
* {
  margin: 0;
  padding: 0;
  list-style: none;
  vertical-align: baseline;
}

div {
  position: relative;
  z-index: 2;
}
body {
  background-color: #333;
  color: #333;
  font-family: 'Raleway', sans-serif;
  font-weight: 400;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
.footer a {
  font-weight: 500;
  text-decoration: none;
  color: #fff;
}

#quote-box {
  border-radius: 3px;
  position: relative;
  width: 450px;
  padding: 40px 50px;
  display: table;
  background-color: #fff;
}
#quote-box .quote-text {
  text-align: center;
  width: 450px;
  height: auto;
  clear: both;
  font-weight: 500;
  font-size: 1.75em;
}
#quote-box .quote-text i {
  font-size: 1em;
  margin-right: 0.4em;
}
@quote-box .quote-author {
  width: 450px;
  height: auto;
  clear: both;
  padding-top: 20px;
  font-size: 1em;
  text-align: right;
}
#quote-box .buttons {
  height: 38px;
  border: none;
  border-radius: 3px;
  color: #fff;
  background-color: #333;
  outline: none;
  font-size: 0.85em;
  padding: 8px 18px 6px 18px;
  margin-top: 30px;
  opacity: 1;
  cursor: pointer; 
}
#quot-box .button .button:hover {
  opacity: 0.9;
}
#quote-box .buttons .button#tweet-quote,
#quote-box .buttons .button#tumblr-quote {
  float: left;
  padding: 0px;
  padding-top: 8px;
  text-align: center;
  font-size: 1.2em;
  margin-right: 5px;
  height: 30px;
  width: 40px;
}
#quote-box .buttons .button#new-quote {
  float: right;
}


💻💻💻JAVASCRIPT CODE💻💻💻(❁´◡`❁)(❁´◡`❁)(✿◡‿◡)();

/* eslint-disable max-len */
// eslint-disable-next-line no-unused-vars
const projectName = 'random-quote-machine';
let quotesData;

/*
  Code by AbhiCoder08
  Modified by Todd Chaffee to use Camper gist for JSON Quote data.
*/

var colors = [
  '#16a085',
  '#27ae60',
  '#2c3e50',
  '#f39c12',
  '#e74c3c',
  '#9b59b6',
  '#FB6964',
  '#342224',
  '#472E32',
  '#BDBB99',
  '#77B1A9',
  '#73A857'
];
var currentQuote = '',
  currentAuthor = '';

function getQuotes() {
  return $.ajax({
    headers: {
      Accept: 'application/json'
    },
    url: 'https://gist.githubusercontent.com/camperbot/5a022b72e96c4c9585c32bf6a75f62d9/raw/e3c6895ce42069f0ee7e991229064f167fe8ccdc/quotes.json',
    success: function (jsonQuotes) {
      if (typeof jsonQuotes === 'string') {
        quotesData = JSON.parse(jsonQuotes);
        console.log('quotesData');
        console.log(quotesData);
      }
    }
  });
}

function getRandomQuote() {
  return quotesData.quotes[
    Math.floor(Math.random() * quotesData.quotes.length)
  ];
}

function getQuote() {
  let randomQuote = getRandomQuote();

  currentQuote = randomQuote.quote;
  currentAuthor = randomQuote.author;

  $('#tweet-quote').attr(
    'href',
    'https://twitter.com/intent/tweet?hashtags=quotes&related=freecodecamp&text=' +
      encodeURIComponent('"' + currentQuote + '" ' + currentAuthor)
  );

  $('#tumblr-quote').attr(
    'href',
    'https://www.tumblr.com/widgets/share/tool?posttype=quote&tags=quotes,freecodecamp&caption=' +
      encodeURIComponent(currentAuthor) +
      '&content=' +
      encodeURIComponent(currentQuote) +
      '&canonicalUrl=https%3A%2F%2Fwww.tumblr.com%2Fbuttons&shareSource=tumblr_share_button'
  );

  $('.quote-text').animate({ opacity: 0 }, 500, function () {
    $(this).animate({ opacity: 1 }, 500);
    $('#text').text(randomQuote.quote);
  });

  $('.quote-author').animate({ opacity: 0 }, 500, function () {
    $(this).animate({ opacity: 1 }, 500);
    $('#author').html(randomQuote.author);
  });

  var color = Math.floor(Math.random() * colors.length);
  $('html body').animate(
    {
      backgroundColor: colors[color],
      color: colors[color]
    },
    1000
  );
  $('.button').animate(
    {
      backgroundColor: colors[color]
    },
    1000
  );
}

$(document).ready(function () {
  getQuotes().then(() => {
    getQuote();
  });

  $('#new-quote').on('click', getQuote);
});
 
