1. arguments, 

```
function(){
    //return:["ar", "br", "cr", callee: ƒ, Symbol(Symbol.iterator): ƒ]
    console.log(arguments);
    //return a slice: ["ar", "br", "cr"]
    console.log(Array.prototype.slice.call(arguments));
}
abc('ar',"br","cr");
```

2. we want define arr.display();

```
var arr = ['ar',"br","cr"];
Array.prototype.display = function(){
  //display array
  console.log(this);
  return this.concat(this);
}

arr.display();

console.log(arr.display());
//display arr twice in a array: ["ar", "br", "cr", "ar", "br", "cr"]
```

3. 
```
function abc(){
  var username = "xy",
      place = "nj";
      var display = function(){
        return username +","+ place;
      }
    return display;
}

document.write(abc()());

//or
var fn = abc();
document.write(fn());
```

4. promise 
```
function abc(){
  var promise = new Promise(function(resolve,reject){
    setTimeout(function(){
      resolve('display');
      //reject(some http err, maybe)
    },3000);
  });
  return promise;
}

var resp = abc();
//first func handles resolve, second handles reject
resp.then(function(data){
  console.log("data,"+data);
},
function(err){
  console.log(err);
})
```

5. jQuery
```
//both work
//using on so that we can add handler to dynamic element
jQuery(document).ready(function(){
  
});

jQuery(document).on('click',"#btn",function(){
  
});
```

6. event binding on element
```
//ready(), on() both work here, using on so that we can add handler to dynamic element
// jQuery(document).ready(function(){
  
// });

var arr =[
    {"username":"xy1","place":"p1","phone":"2123123"},
    {"username":"xy2","place":"p2","phone":"2123123"},
    {"username":"xy3","place":"p3","phone":"2123123"},
    {"username":"xy4","place":"p4","phone":"2123123"},
    {"username":"xy5","place":"p5","phone":"2123123"}
    ];

jQuery(document).on('click',"#btn",function(){
  
  var len = arr.length,
      htm = '<table border="1"><tr><th>Username</th><th>Place</th></tr>';
  for(let i = 0; i <len; i++){
    htm +="<tr id = 'tr_"+i+"'><td>"+arr[i].username+"</td>";
    htm +="<td>"+arr[i].place+"</td>";
    htm +="<td><a href = '#' id = 'view_"+i+"' tab = "+i+">view details</a></td>";
    htm +="</tr>";
  }
  htm+="</table>"
  jQuery('#tab').html(htm);
  jQuery('#para').html('mar');
  
});

jQuery(document).on('click','a[id^="view_"]',function() {
  // console.log('hh');
  // alert(jQuery(this).attr('tab'));

  //add he1, he2 to the same place, he3 in tr before he2he1
  //??
  var id = jQuery(this).attr('tab');
  console.log("id"+id);
  jQuery('#tr_'+id).after('he1');
  
  var thisObj = jQuery(this).parent().parent();
  thisObj.after('he2');
  console.log("thisObj"+thisObj);

  var htm2 = "<tr><td colspan='3'>he3</td></tr>";
  thisObj.after(htm2);
});
```











//assignment, create abc
abc(2)(3)(4)
//download mangodb, terminal, mongod to check if you install mangodb successfully
```
function abc(a){
  return function(b){
     console.log("a+b",a+b);
    return function(c){
      console.log("all:",a,b,c);
      return a+b+c;
    }
  }
}

console.log("final:",abc(2)(3)(4));
```
