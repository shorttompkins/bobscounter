# Bob's Counter

## To Use:
 * Include `countup.min.js` in the page (before the snippet)
 * Include the following code snippet:


 ````javascript
 <script type="text/javascript">
   // CONFIGURATION OPTIONS: //
   // ---------------------- //
   var startTime = new Date('3/1/2017'),
     startAmount =      1400000000,
     incrementAmount =  154,
     min_recount =      2500,
     max_recount =      6500,
     animate_from =     0

   // ***********************************************************************//
   // DONT TOUCH BELOW!! //
   // ***********************************************************************//
   var nowTime = new Date(Date.now()),
     sinceTime = Math.abs((startTime.getTime() - nowTime.getTime()) / 1000),
     startTotal = startAmount + (sinceTime * incrementAmount);

   var numAnim = new CountUp("counter", animate_from, startTotal);
   numAnim.start(startUpdateTimer);

   function startUpdateTimer() {
     var nextUpdate = Math.floor(Math.random() * (max_recount - min_recount)) + min_recount;
     window.setTimeout(function(){
       newNowTime = new Date(Date.now());
       sinceTime = Math.abs((nowTime.getTime() - newNowTime.getTime()) / 1000),
       newTotal = startTotal + (sinceTime * incrementAmount);
       numAnim.update(newTotal);
     }, nextUpdate);
   }

 </script>
 ````

## Configuration Options:

 - `startTime:` 3/1/2017 - can be any date, just increases the total amount you see when the page loads
 - `startAmount:` 1400000000  - the starting balance as of the date above. The amount of seconds between the `startTime` and now will be computed using `incrementAmount` (below) and then added onto the `startAmount`
 - `incrementAmount:` 154 - the total lbs to increment per second (both from the `startTime` and every iteration forward).
 - `min_recount`, `max_recount` - range in milliseconds that the counter will randomly update with the new total.
 - `animate_from` 0 - the starting value of the main counter the instant the page loads. 0 = super fast counter since it needs to get up to the grand total and thats a large number. The larger this starting number is the slower the animation countUp period will appear to be. (in the future, its best to increase this amount so the countUp isn't trying to animate from 0 - 10,000,000,000 for example)
