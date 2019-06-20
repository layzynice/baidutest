<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <style>
    .palette {
        margin: 0;
        padding: 0;
        list-style: none;
    }
    .palette li {
        width: 40px;
        height: 40px;
        border: 1px solid #000;
        cursor: pointer;
    }
</style>
</head>
<body>
<input type="text" id="name">
<button id="submit-btn">Submit</button>
<script>
  let btn = document.getElementById('submit-btn')
  btn.onclick=function() {
    console.log(document.getElementById('name').value)
  }
  let name = document.getElementById('name');
  name.onkeyup= function(e) {
    let event = e || window.event;
    let key = event.which || event.keyCode || event.charCode;
    if (key == 13) console.log(this.value)
    if (key === 27 ) this.value = ''
  }
</script>
<label>
  <input id="school" name="status" type="radio">
  School
</label>
<label>
  <input id="company" name="status" type="radio">
  Company
</label>

<select id="school-select">
  <option>北京邮电大学</option>
  <option>黑龙江大学</option>
  <option>华中科技大学</option>
</select>

<select id="company-select">
  <option>百度</option>
  <option>爱奇艺</option>
</select>
<script>
  let school = document.getElementById('school');
  let school_select = document.getElementById('school-select');
  let company = document.getElementById('company');
  let company_select = document.getElementById('company-select');
  school.onchange = function () {
    if (school.checked) {
      school_select.style.display = 'block';
      company_select.style.display = 'none'
    }
  }
  company.onchange = function () {
    if (company.checked) {
      school_select.style.display = 'none';
      company_select.style.display = 'block'
    }
  }
</script>
<ul class="palette">
  <li style="background-color:crimson"></li>
  <li style="background-color:bisque"></li>
  <li style="background-color:blueviolet"></li>
  <li style="background-color:coral"></li>
  <li style="background-color:chartreuse"></li>
  <li style="background-color:darkolivegreen"></li>
  <li style="background-color:cyan"></li>
  <li style="background-color:#194738"></li>
</ul>

<p class="color-picker"></p>
<script>
  let list = document.querySelectorAll("li");
  let p = document.querySelector('.color-picker');
 /*  for (let i = 0; i < list.length; i++) {
    list[i].onclick = function() {
      let bgColor = this.style.backgroundColor;
      p.innerHTML = bgColor;
      p.style.color = bgColor;
    }
  } */
  /*  直接使用事件委托 把li上的点击事件委托给 ul */
  let ul = document.querySelector('.palette')
  ul.onclick = function (ev) {
    var ev = ev || window.event;
    var target = ev.target || ev.srcElement;  // target就可以表示为当前的事件操作的dom，但是不是真正操作dom  ev.target || IE浏览器ev.srcElement
    let bgColor = target.style.backgroundColor;
      p.innerHTML = bgColor;
      p.style.color = bgColor;
  }
</script>
</body>
</html>
