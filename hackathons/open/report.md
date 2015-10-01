# Report
{% data src="bs.json" %}
{% enddata %}

Use only Javascript and SVG to produce a data analysis / visualization report.

# Authors

This report is prepared by
* [Fadhil Suhendi](link to github account)
* [Heather Witte](link to github account)


<a name="top"/>
<div id="autonav"></div>

{% viz %}

{% title %}

# What are the condition:precipitation when birdstrike occur?

{% solution %}

var group = _.groupBy(data,function(n){
  return n['Conditions: Precipitation']
})

var gro = _.mapValues(group,function(d){
  return d.length
})

var newgroup = _.map(gro, function(v,k){
  return {"conditions": k, "numbers":v}
})

_.remove(newgroup,function(value){
  return value.conditions == ''
})

console.log(newgroup)

// TODO: modify the code below to produce a nice vertical bar charts

function computeX(d, i) {
    return 50
}

function computeHeight(d, i) {
    return 20
}

function computeWidth(d, i) {
    if(d.numbers > 40000){
      return d.numbers * (300 / 40000)
    }else if(d.numbers > 800 && d.numbers < 3000) {
      return d.numbers * (200/ 3000)
    }else if(d.numbers < 200) {
      return d.numbers * (200/2000)
  }
}

function computeY(d, i) {
    return i * 20 + 20
}

function computeYText(d,i) {
  return i * 20 + 35
}

function computeColor(d, i) {
    return 'red'
}

function computeLabel(d,i) {
    return d.conditions
}

var viz = _.map(newgroup, function(d, i){
            return {
                x: computeX(d, i),
                y: computeY(d, i),
                ty: computeYText(d,i),
                height: computeHeight(d, i),
                width: computeWidth(d, i),
                color: computeColor(d, i),
                label: computeLabel(d,i)
            }
         })
console.log(viz)

var result = _.map(viz, function(d){
         // invoke the compiled template function on each viz data
         return template({d: d})
     })
return result.join('\n')

{% template %}
    <rect x="120"
          y="${d.y}"
          height="20"
          width="${d.width}"
          style="fill:${d.color};
                 stroke-width:3;
                 stroke:rgb(0,0,0)" />
    <text transform="translate(0 ${d.ty})">${d.label}</text>

{% endviz %}




