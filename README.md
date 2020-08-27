# Local Session Storage

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/0.100.2/css/materialize.min.css">
  <link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet" integrity="sha384-wvfXpqpZZVQGK6TAh5PVlGOfQNHSoD2xbE+QkPxCAFlNEevoEH3Sl0sibVcOQVnN"
    crossorigin="anonymous">
  <title>Task List</title>
</head>

<body>
  <div class="container">
    <div class="row">
      <div class="col s12">
        <div id="main" class="card">
          <div class="card-content">
            <span class="card-title">Task List</span>
            <div class="row">
              <form id="task-form" action="index.php">
                <div class="input-field col s12">
                  <input type="text" name="task" id="task" value="">
                  <label for="task">New Task</label>
                </div>
            </div>
            <button id="add" class="btn">Add</button>
            </form>
          </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <script src="https://code.jquery.com/jquery-3.2.1.js" integrity="sha256-DZAnKJ/6XZ9si04Hgrsxu/8s717jcIzLy3oi35EouyE=" crossorigin="anonymous"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/0.100.2/js/materialize.min.js"></script>
  <script src="app.js"></script>
</body>

</html>
```

## Local Storage

### Storage

_console_
`window`

![image](https://user-images.githubusercontent.com/69710213/91370010-cbeb4a80-e83f-11ea-94a9-bef5f90002e1.png)

---

**Local Storage and Session Storage differences**

    - local storage will stay until you manually clear it out on your setting, or to your programme.

    - session storage, will leave or go away once your browser close, once the session is close

---

**set local storage item**

```javascript
localStorage.setItem('name', 'John');
```

![image](https://user-images.githubusercontent.com/69710213/91370794-db6b9300-e841-11ea-8c5d-8690340237b1.png)

```javascript
localStorage.setItem('age', '30');
```

---

**remove from storage**

```javascript
localStorage.removeItem('name');
```

![image](https://user-images.githubusercontent.com/69710213/91371055-98f68600-e842-11ea-96cb-8b15743421ef.png)

---

**set session storage item**

```javascript
sessionStorage.setItem('name', 'Beth');
```

![image](https://user-images.githubusercontent.com/69710213/91370893-25547900-e842-11ea-9ef0-4c583c63bee6.png)

---

// get from storage

```javascript
const name = localStorage.getItem('name');
console.log(name);
```

![image](https://user-images.githubusercontent.com/69710213/91371431-8b8dcb80-e843-11ea-9b4f-4fcfd4811a0c.png)

```javascript
const age = localStorage.getItem('age');
console.log(name, age);
```

![image](https://user-images.githubusercontent.com/69710213/91371510-cb54b300-e843-11ea-85c6-2bff137e33b4.png)

---

**clear local storage**

```javascript
localStorage.clear();
```

![image](https://user-images.githubusercontent.com/69710213/91371774-8d0bc380-e844-11ea-8170-a81543f67704.png)

---

**Submit Event**

```javascript
document.querySelector('form').addEventListener('submit', function (e) {
	const task = document.getElementById('task').value;
	let tasks;

	if (localStorage.getItem('tasks') === null) {
		tasks = [];
	} else {
		tasks = JSON.parse(localStorage.getItem('tasks'));
	}

	tasks.push(task);

	localStorage.setItem('tasks', JSON.stringify(tasks));

	alert('Task saved');

	e.preventDefault();
});

const tasks = JSON.parse(localStorage.getItem('tasks'));

tasks.forEach(function (task) {
	console.log(task);
});
```
