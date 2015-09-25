{% data src="bs.json" %}
{% enddata %}

# Report

As a team, answer a subset of the questions submitted during the hackathon.
But instead of using Tableau, you will need to write Javascript/Lodash code
to derive your answers. Similar to before, each team member is responsible for
one question. But everyone should work together to come up with a good solution.
Your answer should consist of Lodash code and a brief writeup.
Utilize `_.map`, `_.filter`, `_.group` ...etc. Do not se any for loop.

This time, the data is not already prepared for you in a nice JSON format. You
will need to do it on your own, replacing the placeholder `birdstrike.json` with
real data.

# Which airlines have the worst luck with birdstrikes in terms of damage caused? 
This question was asked by (calebhsu).

{% lodash %}

{% endlodash %}


# What is the most common flight phase where a birdstrike occurred?
This question was asked by (KevinKGifford).

{% lodash %}

var group = _.groupBy(data,function(n){
	return n["When: Phase of flight"]
})

var result = _.mapValues(group,function(n){
	return _.map(n,function(d){
		return d["When: Phase of flight"]
	}).length
})


return result
{% endlodash %}

<table>
{% for key, value in result %}
    <tr>
        <td>{{key}}</td>
        <td>{{value}}</td>
    </tr>
{% endfor %}
</table>


# What airports have the most expensive average accident?

This question was asked by (satchelspencer ).

{% lodash %}

return "[answer]"
{% endlodash %}

# Which plane strikes the most birds?

This question was asked by (twagar95).

{% lodash %}
return "[answer]"
{% endlodash %}

# What state had the highest number of bird strikes? (Departure State)

This question was asked by (drewdinger).

{% lodash %}
return "[answer]"
{% endlodash %}
