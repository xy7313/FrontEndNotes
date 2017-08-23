1. 
```
 <script src="https://google.github.io/traceur-compiler/bin/traceur.js"></script>
<script src="https://google.github.io/traceur-compiler/bin/BrowserSystem.js"></script>
<script src="https://google.github.io/traceur-compiler/src/bootstrap.js"></script>   
```

2.  let keywrod. it only visible for the block it was created
```
if(true){
  var username = "xy";
  let cntr = 0;
}
document.write(cntr);
```

```
for(let i=0;...){
    //use let here
}
```

3. const keyword, can not be changed after definde
```
const ORG = "xy";
const ORG = "xy";
document.write(ORG);
//get an error: Identifier 'ORG' has already been declared
```

4. a new syntax
```
var arr = ['ar','xy','hi'];

//var username = arr[0];
var [username,org,place]= arr;

document.write(username);
//output: ar
```
or
```
function retData(){
  var arr = ['ar','xy','hi'];
  return arr;
};

var [username,org,place]= retData();
//we also can: var [ , ,place] = retData();
document.write(username);
```
or
```
var userObj = {
  fn:"x",
  ln:"y",
  pl:"nj"
};

var {
  fn:fname,
  ln:lname,
  pl:place
} = userObj;

document.write(fname);
document.write(lname);
document.write(place);
//output: xynj
```

5. default value of parameters
```
//given default value at below
function abc(username="x",org="m"){

  return 'un='+username+',org='+org;
}

var resp = abc();
//var resp = abc('newname',''newplace);

document.write(resp);
```

6. arrow function
```
//old
function add(x,y){
  return x+y;
}
//new in es6
var add_new= (x,y)=>x+y;
//or
var add_new= (x,y)=>{
  return x+y;
}
document.write(add_new(4,5));
```

7. using\` back tic
```
function add(x,y){
  // return "x:"+x+",y:"+y;
  //` here
  return `x:${x}`;
}

document.write(add(4,5));
```

8. create class
```
class user{
  getData(){
    return "xx";
  }
}

var user1 = new user();

console.log(user1.getData());
```

9. constructor, child class, super, if we have constructor in child class, we must call super

```
class user{
  //constructor
  constructor(username){
      this.uname = username;
  }
  
  getData(){
    return "hi"+this.uname;
  }
}

class emp extends user{
  constructor(empCode,org){
    super(org);
    this.emp_code = empCode;
  }
  getEmpCode(){
    return "empcode:<br />"+this.emp_code;
  }
  getData(){
    return super.getData();
  }
}

//example before we have constructor in child class, we can use the code committed

var user1 = new user("xyyy<br />");
// var emp1 = new emp("emmm<br />");
var emp2 = new emp("1<br />","emp2");

document.write(user1.getData());
// document.write(emp1.getData());
document.write(emp2.getEmpCode());
document.write(emp2.getData());
```

10. Set
```
var set1 = new Set(),
  arr = ["1","2","3"],
  obj = {"un":"xy"};
  
set1.add("ar");
set1.add(arr);
set1.add(obj);

set1.has(obj);

set1.forEach(function(value){
  document.write(value+"<br />hi");
});

document.write(set1);
document.write(set1.has(obj));
set1.clear();
document.write(set1.has(obj));
/...true, false
```

11. map
```
var map1 = new Map();
var obj = {
  "fn":"xy"
};

map1.set("un","ar");
map1.set(obj,true);

map1.forEach(function(value,key){
  document.write("k:"+key+",v:"+value+"<br />");
});

console.log(map1);
document.write(map1.get("un"));
//output:k:un,v:ar-k:[object Object],v:true-ar
```

12. promise
```
var promise1 = new Promise(function(resolve,reject){
  resolve('1');
});
var promise2 = new Promise(function(resolve,reject){
  reject('2');
});
var promise3 = new Promise(function(resolve,reject){
  resolve('3');
});

Promise.all([promise1,promise2,promise3]).then(function(data){
  console.log(data);
},
function(err){
  console.log(err);
});
//output:["1","2","3"](when all resolve)
//output:2, when as above, promise2: reject
//output:1, when Promise.all-->Promise.race
```

13. import module
```
//index.html
<script type = "module" src="script.js"></script>

//script.js
import {abc, user_arr, user} from './mod.js';
document.write(user.fn);
//or use this:
import * as moduleContent from './mod.js';
document.write(moduleContent.user.fn);

//mod.js
export function abc(){
  return 'hello';
}

export var user_arr = ['ar','na'];

export var user = {
  fn:"x",
  ln:"y",
  pl:"nj"
}
//or export everything in one line
export {abc, user_arr, user}
```

4. arguments, advanced arguments
```
// import * as moduleContent from './mod.js';

// document.write(moduleContent.user.fn);


function abc2(...args){
  console.log("2:"+args);
}

function abc1(){
  console.log("1:"+arguments);
}

function abc3(...[username,org]){
  console.log("3:"+username+","+org);
}

//??
function abc4(para1,phone,...[username,org]){
  console.log("4:"+username+","+phone);
}

abc1("1","2");
abc2("1","2");
abc3("1","2","3");
abc4("ar","ma","pi","99");

var arr = ["010","020"];
var newa = ["1",...arr,"2"];
console.log(newa);
```