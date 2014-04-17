---
title: batchFind
signature: |
    states.batchFind([<hashkey>, <hashkey>]) ⇒ promise
    counties.batchFind([{hash: <hashkey>, range: <rangekey>}, {hash: <hashkey>, range: <rangekey>}, ... ]) ⇒ promise
---

Find multiple items in batch via a single call. That is find all the
items in a table associated with a hash key.

Promise resolves with an array including all items matching your search.

{% highlight js %}
// Simplest case, table with only hash keys:
var promise = states.batchFind(['Virginia', 'Maryland', 'New York']);

promise.then(function(states) {
    states.forEach(function(state) {
        console.log(state.population);
    });
});

// More complex case, table with hash and range keys
counties
    .batchFind([{hash: 'Ireland', range: 'Cork'}, {hash: 'Ireland', range: 'Galway'}])
    .then(function(result) {
        result.forEach(function(county) {
            console.log(county);
        });
    });

{% endhighlight %}
