# Warmup

Complete this warmup exercise to get an idea how to put all the different pieces
together to generate an end-to-end data analysis viz report.

<a name="top"/>
<div id="autonav"></div>

{% data src="../fcq/fcq.clean.json" %}
{% enddata %}

{% viz %}

{% title %}

What is the distribution of courses across colleges?

{% solution %}

<<<<<<< HEAD
var groups = _.groupBy(data, function(d){ return d['CrsPBAColl'] })

// TODO: add real code to convert groups (which is an object) into an array like below 
// This array should have a lot more elements. 
var newGroup = _.mapValues(groups,function(n){
  return n.length
})

var newgr = _.map(newGroup,function(k,v){
  return {"name":v,"count":k}
})
console.log(newgr)
=======
var groups = _.groupBy(data, function(d){
    return d['CrsPBAColl']
})

// TODO: add real code to convert groups (which is an object) into an array like below
// This array should have a lot more elements.
var counts = [{"name": "AS","count": 3237},
    {"name": "BU","count": 378},
    {"name": "EB","count": 139},
    {"name": "EN","count": 573}]

console.log(counts)
>>>>>>> upstream/master

// TODO: modify the code below to produce a nice vertical bar charts

function computeX(d, i) {
    return 0
}

function computeHeight(d, i) {
    return 20
}

function computeWidth(d, i) {
<<<<<<< HEAD
    return d.count
=======
    return 20 * i + 100
>>>>>>> upstream/master
}

function computeY(d, i) {
    return 20 * i
}

<<<<<<< HEAD
function computeYText(d,i) {
  return i * 20 + 16
}

=======
>>>>>>> upstream/master
function computeColor(d, i) {
    return 'red'
}

<<<<<<< HEAD
function computeLabel(d,i) {
  return d.name
}

var viz = _.map(newgr, function(d, i){
=======
var viz = _.map(counts, function(d, i){
>>>>>>> upstream/master
            return {
                x: computeX(d, i),
                y: computeY(d, i),
                height: computeHeight(d, i),
                width: computeWidth(d, i),
<<<<<<< HEAD
                color: computeColor(d, i),
                label: computeLabel(d,i),
                ty:computeYText(d,i)
=======
                color: computeColor(d, i)
>>>>>>> upstream/master
            }
         })
console.log(viz)

var result = _.map(viz, function(d){
         // invoke the compiled template function on each viz data
         return template({d: d})
     })
return result.join('\n')

{% template %}

<<<<<<< HEAD
<rect x="80"
=======
<rect x="0"
>>>>>>> upstream/master
      y="${d.y}"
      height="20"
      width="${d.width}"
      style="fill:${d.color};
             stroke-width:3;
             stroke:rgb(0,0,0)" />
<<<<<<< HEAD
<text transform="translate(0 ${d.ty})">${d.label}</text>
=======
>>>>>>> upstream/master

{% endviz %}
