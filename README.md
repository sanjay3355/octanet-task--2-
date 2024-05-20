# octanet-task--2-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>To Do List</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Times New Roman', Times, serif;
        }
        body {
            width: 100%;
            background-image: linear-gradient(135deg, #4abad8, #2e1d31);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }
        .container {
            width: 100%;
            background-color: #fff;
            min-width: 540px;
            border-radius: 10px;
        }
        .cont1 {
            width: 100%;
            max-width: 540px;
            background: #fff;
            margin: 100px auto 20px;
            padding: 40px 30px 70px;
            border-radius: 10px;
        }
        .cont1 h1 {
            color: #2068dc;
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }
        .cont1 h1 img {
            width: 40px;
            height: 40px;
            margin-left: 10px;
        }
        .add {
            background-color: #edeef0;
            border-radius: 30px;
            display: flex;
            justify-content: space-between;
            margin-bottom: 14px;
        }
        .add input {
            flex-grow: 1;
            border: none;
            outline: none;
            padding: 10px;
            background: transparent;
            font-size: 20px;
        }
        .add button {
            border: none;
            outline: none;
            background-color: #2d2503;
            color: rgb(241, 25, 25);
            border-radius: 40px;
            padding: 16px 50px;
            font-size: 16px;
            cursor: pointer;
        }
        #list-container {
            list-style-type: none;
            display: flex;
            flex-direction: column;
        }
        #list-container li {
            font-size: 20px;
            padding: 10px;
            position: relative;
        }
        #list-container li:hover {
            cursor: pointer;
        }
        #list-container li span {
            border-radius: 50%;
            position: absolute;
            right: 0;
            bottom: 2%;
            font-size: 20px;
            height: 35px;
            width: 35px;
            line-height: 30px;
            padding-top: 3px;
            text-align: center;
        }
        #list-container li span:hover {
            cursor: pointer;
            background-color: rgba(0, 0, 0, 0.197);
            background-size: 100%;
        }
        ul li.checked {
            background-color: rgba(0, 0, 0, 0.129);
            text-decoration: line-through;
            order: 1;
        }
    </style>
</head>
<body>
    <main>
        <div class="container">
            <div class="cont1">
                <h1>To Do List <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQSBaq9XuaYT59Ybm3sBRc0p6C4L7nglQHwDQ&s" height="40" width="40"></h1>
                <div class="add">
                    <input type="text" placeholder="Add Your Task" id="input-box">
                    <button onclick="addTask()">ADD</button>
                </div>
                <ul id="list-container"></ul>
            </div>
        </div>
        <script>
            const inputBox = document.getElementById("input-box");
            const listContainer = document.getElementById("list-container");

            function addTask() {
                if (inputBox.value === "") { 
                    alert("Please Enter Something");
                } else {
                    let li = document.createElement("li");
                    li.innerHTML = inputBox.value;
                    listContainer.appendChild(li);
                    let span = document.createElement("span");
                    span.innerHTML = "\u00D7";
                    li.appendChild(span);
                    saveData();
                }
                inputBox.value = "";
            }

            listContainer.addEventListener("click", function(e) {
                if (e.target.tagName === "LI") {
                    e.target.classList.toggle("checked");
                    saveData();
                } else if (e.target.tagName === "SPAN") {
                    e.target.parentElement.remove();
                    saveData();
                }
            }, false);

            function saveData() {
                localStorage.setItem("data", listContainer.innerHTML);
            }

            function showTask() {
                listContainer.innerHTML = localStorage.getItem("data");
                if (!listContainer.innerHTML) {
                    listContainer.innerHTML = '';
                }
            }

            showTask();
        </script>
    </main>
</body>
</html>
