**Closure**
<pre><code>
    function wrapValue(n) {
      var localVariable = n;
      return function() { return localVariable; };
    }
    
    function multiplier(factor) {
      return function(number) {
        return number * factor;
      };
    }
    
    var twice = multiplier(2);
    console.log(twice(5));
    // → 10
</code></pre>

