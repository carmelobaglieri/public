# Intro

Some of technologies specified in the task, exactly Webpack and templates engine, as said during the interview, they are not in my skills, therefore I could not use them in this small period.
This was my first really complex plugin and, not being in the business, I interpretated the request due my comprension.
Ps: I powered this in twentynineteen theme.


# Files

index.php - Define global vars, import required files, register scripts and styles and add the shortcodes.
/admin/options.php - Add options in db and add a page in Wordpress setting menu.
/admin/sports.json - List of sports, setted with an API call.
/front - Templates html degli shortcode.
/inc/functions.php - Contains the function for API calls, linked with "wp_ajax_" action.
/sass - Compile stylesheet in /css importing also some bootstrap components - compiled with npm.
/css - Stylesheets
/js - Scripts



# Init

After activation the plugin, a valid API key is required valida in setting page.
Here is possible also choose a favourite sport (sports loaded from json and stored in db), an auto-refresh of values loaded on front and adding fontawesome (I know this is not the right way).
The big part of the program is in /js/filters.js.
I created a class with a private variable for useful data, used also based on events.
In the constructor, the sports passed as a value at the time of the enqueue of filters.js and the bet are rendered.



# Main functions

renderBet() this is the real main function.
1. Create a cookie for store bet odds added
2. Do a call based on favourite sport and render the odds (region is init with 'US').
3. The rendering of the added values starts (if any) ordered by start time, therefore based on the bet, precisely on the sport, it makes a call and saves them in the general variable.
4. The stakes and the bet type (single or multiple) and the calculation of the values progressively are also included in the cookie.

renderSports()
1. Rendering of the sports grouped by sport group.
2. Re-rendering when inserting a search key, also applied to the group name.
3. Set favourit sport with new value on click of a sport.
4. Call values if not loaded before, else renderBet() with the values already stored.

addToBet()
1. Add the odd to the bet if not present, else remove it.
2. Update coookie values

getTotalStake() - getTotalWin()
1. They calculate the respective sums based on the values entered in the cookie



# Cookie data - expired in 1 day after last update
{"type":"single","format":"fractal","region":"uk","data":[{"sport":"americanfootball_nfl","match":0,"commence_time":1580685600,"site":"betfair","h2h":0,"h2h_val":"1.870","stake":0,"win":0},{"sport":"aussierules_afl","match":0,"commence_time":1584606300,"site":"ladbrokes","h2h":0,"h2h_val":"4.000","stake":0,"win":0}],"multi_stake":""}



# Filters/settings
Odds format - Set the value view of the odds based on preference
Region - Change region and do a new call



# Conclusions
I thought the calculator was the bet slip.
In any case it is always possible to view the first calculator I made using the shortcode [odds_calculator] instead of [bet_calculator]
I hope I have left everything out and not left anything out, but above all I hope I am not off topic.
