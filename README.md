# Python-FLASK To Do App

![Website Demo][website-image]

## Requirements
-python
-flask
-sqlalchemy
-flask_sqlalchemy
-Jinja 2

## Sections
- [Python-FLASK To Do App](#python-flask-to-do-app)
  - [Requirements](#requirements)
  - [Sections](#sections)
  - [Header](#header)
  - [Make Sure You Have Python Installed!](#make-sure-you-have-python-installed)
  - [Routing](#routing)

## Header 
___
This To-Do App is made using Flask Python Framework. The data on the To-Do App is directly store on an SQLite3 Database file. Any changes(update/delete) to the The To-Do's can will remain. The changes will then be reflected on to the To-Do's App. This allows you to customize your own personal To-Do's that can be used for applying to jobs or other personal uses.

## Make Sure You Have Python Installed!
___
Firstly, you will need to download python
Secondly, you will have to pull all the installed libraries from **requirements.txt**

```
    $ pip install -r requirements.txt
```

[website-image](https://todoflaskapptestional.herokuapp.com/)

## Routing
___

```python
@app.route('/', methods=['POST', 'GET'])
def index():
    if request.method == 'POST':
        task_content = request.form['content']
        new_task = Todo(content=task_content)

        try:
            db.session.add(new_task)
            db.session.commit()
            return redirect('/')
        except:
            return "There was an error adding you data to the Todo App"

    else:
        tasks = Todo.query.order_by(Todo.date_created).all()
        return render_template('index.html', tasks=tasks)
```

**TODO** Host To-DO App Online
___

- using gunicorn server
  ```
  $ pip install gunicorn
  ```
- Go to Heroku and set up a profile
**Reminder** You need to have Git installed then Heroku-setup

-[heroku docs](https://devcenter.heroku.com/articles/heroku-cli)
-[git docs](https://git-scm.com/video/what-is-git)
