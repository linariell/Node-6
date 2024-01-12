<p></p>

<h2 align="center">ФЕДЕРАЛЬНОЕ ГОСУДАРСТВЕННОЕ БЮДЖЕТНОЕ ОБРАЗОВАТЕЛЬНОЕ УЧРЕЖДЕНИЕ ВЫСШЕГО ПРОФЕССИОНАЛЬНОГО ОБРАЗОВАНИЯ <br> «САХАЛИНСКИЙ ГОСУДАРСТВЕННЫЙ УНИВЕРСИТЕТ» <br> КАФЕДРА ИНФОРМАТИКИ </h2>
<p align="center">Лабораторная работа №6 <br>
по курсу «Web-технологии, языки и средства создания web-приложений» 

<p align="center"><b>"Node.js"</b><p>
<p align="right"><b>Выполнила: </b> студентка 331 группы Витковская Полина</p>
<p  align="right"><b>Принял: </b> Соболев Е. И., старший преподователь</p>
<br>
<br>
<br>
<p align="center">Южно-Сахалинск <br> СахГУ <br> 2024</p>
<h2> Введение </h2>
<p>Лабораторные работы по дисциплине «Web-технологии, языки и средства создания web-приложений» предназначены для освоения полученных теоретических знаний на практике. Перед началом лабораторной работы были поставлены цели: <br>
<ol>
  <li>Овладеть навыками работы с node.js. Используя Java Script, решить задачи.
</ol>
В соответствии с данными целями необходимо решить следующие задачи:
<ol>
   <li> Написать скрипты для решения данных задач.
   </ol>
Для реализации данной работы будет использоваться Visual Studio Code. Выполнение кода будет происходить в браузере Google Chrome с использованием node.js.
</p>
<h2>Решение задач</h2>
<p>Файл, запускающий сервер на node.js: </p>

```javascript
const express=require("express");
const hbs = require('hbs');
const pug = require('pug');
const ejs = require('ejs');
const app=express();

app.use(express.static(__dirname));
app.use("/",function(request,response) {
    response.sendFile("C:\\Users\\pvitk\\Desktop\\школа\\3курс\\Вебы\\lab6\\abs.html")
});
hbs.registerPartials(__dirname + "/views/partials");
app.use(express.static(__dirname + "/public"));

app.get("/me/hbs", function(req, resp){
    app.set("view engine", "hbs");
    resp.render(__dirname+'/views/me.hbs');
});

app.get("/me/pug", function(req, resp){
    app.set("view engine", "pug");
    resp.render(__dirname+'/views/pug/me.pug');
});

app.get("/me/EJS", function(req, resp){
    app.set("view engine", "ejs");
    resp.render(__dirname+'/views/me.ejs');
});
app.listen(3001);
console.log('Сервер работает');

```
<p>HTML файл:</p>

```javascript
 <!DOCTYPE html>
<html lang="en">
   
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>Лабораторная 6</h1>
    <p>
        <button onclick="alert('alert!!')">Задача 1</button>
    </p>
    <p>
        <button onclick="func2()">Задача 2</button>
    <input type="text" id="input2" value="Input">
    </p>
    <p>
        <button onclick="func3()">Задача 3</button>
        <input type="text" id="input3" value="Third">
    </p>
    <p>
        <button onclick="func4()">Задача 4</button>
        <input type="number" id="input4" value="2">
    </p>
    <p>
        <button onclick="func5()">Задача 5</button>
        <input type="text" id="input51" value="first">
        <input type="text" id="input52" value="second">
    </p>
    <p>
        <button onclick="this.innerHTML = 'Другой текст'">Задача 6</button>
        
    </p>
    <p>
        <button onclick="func7()">Задача 7</button>
        <input type="text" id="Input7" value="Red">
    </p>
    <p>
        <button onclick="func8()">Задача 8 Блок</button>
        <button onclick="func82()">Задача 8 Разблок</button>
        <input type="text" id="Input8" value="input8">
    </p>

    <p>
        <button onmouseover="alert('Вы погладили кнопочку')">Задача 9</button>
      </p>
<p>
    <button ondblclick="alert('двойное нажатие')">Задача 10</button>
</p>
<p>
    <div class="z11" style="border: 2px solid black;width: 100px;height: 30px;background-color: pink;text-align: center;;" onmouseover="alert('Погладили див ')">Задача 11</div>
</p>

<p>
        <button onclick="func12()">Задача 12</button><br>
        <img id="myImage" src="0d0d9965cd3a9b7be059b2356a65057e.jpg" width="200" height="200">
</p>

<p>
    <button onclick="alert(this.innerHTML)">Задача 13</button>
</p>
<p>
    <input type="text" id="Input14" value="input14">
  <button onclick="this.previousElementSibling.value = 'Изменили'">Задача 14</button>
</p>
<p>
    <button onclick="this.disabled=true;">Задача 15</button>
</p>
<p>
    <button onclick="func16()">Задача 16</button>
    <p id="clickCount">Нажали: 0</p>
</p>

<p>
  <button onclick="this.style.cursor = 'pointer'">Задача 17</button>
</p> 
<p>
    <button onclick="func18()">Задача 18</button>
    <p id="hide">id=hide</p>
</p>
<p>
    <button onclick="this.style.display = 'none'">Задача 19</button>
</p>
<p>
    <p>Задание 20</p>
    
    <input type="number" id="first" value="2">
    <button onclick="plus()">+</button>
    <button onclick="minus()">-</button>
    <button onclick="mult()">*</button>
    <button onclick="div()">/</button>
    <input type="number" id="second" value="4">
    

</p>
<script>
   

function func2()
{
 var input = document.getElementById('input2');
 input.value = "Ne input";
}
 function func3() {
 alert(document.getElementById('input3').value);
}

function func4() {
  alert(Math.pow(document.getElementById('input4').value, 2))
}

function func5() {
  var temp = document.getElementById('input51').value; 
  document.getElementById('input51').value = document.getElementById('input52').value; 
  document.getElementById('input52').value = temp;
}

function func7() {
  document.getElementById('Input7').style.color ="red"
}

function func8() {
  document.getElementById('Input8').disabled = true;
    }
    function func82() {
      document.getElementById('Input8').disabled = false;
        }







    function func12() {
      document.getElementById('myImage').src = "photo_2022-09-15_10-38-52.jpg";
    }

var clickCount = 0;
function func16() {

  clickCount++;
  document.getElementById("clickCount").innerHTML = "Нажали: " + clickCount;
  }   

function func18() {
  
    document.getElementById('hide').style.display = 'none';

}
function plus()
{
    let a=parseInt( document.getElementById("first").value);
    let b=parseInt(document.getElementById("second").value);
    alert(a+b);
}
function minus()
{
    let a=parseInt( document.getElementById("first").value);
    let b=parseInt(document.getElementById("second").value);
    alert(a-b);
}
function mult()
{
    let a=parseInt( document.getElementById("first").value);
    let b=parseInt(document.getElementById("second").value);
    alert(a*b);
}
function div()
{
    let a=parseInt( document.getElementById("first").value);
    let b=parseInt(document.getElementById("second").value);
    if(a==0) {alert("Неопределенность")}
    else if(b==0) {alert("Деление на ноль!")}
    else {let res=a/b; alert(res);}
    
}
    </script>
</body>
</html>

```
<p>CodeWars:</p>

```javascript
function checkCoupon(enteredCode, correctCode, currentDate, expirationDate){
  let date1 = new Date(currentDate);
  let date2 = new Date(expirationDate);
  return enteredCode === correctCode && date1 <= date2;
}

function unluckyDays(year){
  let result = 0;
  for(let i = 0; i < 12; i++)
  {
    if(new Date(year, i, 13).getDay() == 5)
      result++;
  }
  return result;
}

function handAngle (date) {
  var pi2 = Math.PI*2;
  var m = date.getMinutes()/60, h = (date.getHours()+m)/12;
  
  var angle = Math.abs(h-m)*pi2;
  return Math.min( angle, pi2-angle )

}

function myLanguages(results) {
  let array = [];
  
  for(var i in results){
    if(results[i] >= 60) array.push(i);
  }
 
  for(var i = 0; i < array.length - 1; i++)
  {
    for(var j = i + 1; j < array.length; j++)
      {
        if(results[array[i]] < results[array[j]])
        {
          temp = array[i];
          array[i] = array[j];
          array[j] = temp;
        }
      }
  }
   return array;
  
}

var runLengthEncoding = function(str){
  if(str.length == 0) return [];
  let result = [];
  let count = 1;
  let char = '';
  for(let i = 0; i < str.length - 1; i++)
  {
    char = str[i];
    if (char == str[i + 1]) count++;
    else{
      result.push([count, char]);
      count = 1;
      char = str[i+1];
    }
  }
  
  result.push([count, char]);
  
  return result; 
}

function find(object, path) {
    let array_path = path.split('.');
    let current_obj = object;
    for(let i = 0; i < array_path.length; i++)
    {
      if(Object.keys(current_obj).includes(array_path[i]))
        current_obj = current_obj[array_path[i]];
      else
        return undefined;
    }
    return current_obj;
}
```
<h2>Вывод</h2>
<p>В ходе лабораторной работы были решены задачи на Java Script, выполнены задачи с Codewars, научились работать с pug, hbs, ejs. Выполнение происходило с помощью Node.js</p>
