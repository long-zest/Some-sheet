# Some-sheet

#Merge array without dub

//not object array
var a = [1, 2, 3], b = [101, 2, 1, 10]
var c = a.concat(b.filter((item) => a.indexOf(item) < 0))

console.log(c) // c is [1, 2, 3, 101, 10]

//with object array
const something = [{id: 1, "name": "somehting"}, {id: 2, "name": "gido"}]
const something2 = [{id: 3, "name": "somehting"}, {id: 4, "name": "gido"}, {id: 2, "name": "gido"}, , {id: 1, "name": "gido"}]

const something3= something.concat(something2.filter(item => !something.some(element => element.id === item.id)))

console.log(something3)


