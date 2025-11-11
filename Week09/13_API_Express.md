# Project Initialization

```
npm init -y
npm i express
npm i sqlite3
npm i --save-dev nodemon
```

# Step 0: index.js
![image](https://hackmd.io/_uploads/ByVjA6fdge.png)

on line #9, within the quotes:
`CREATE TABLE IF NOT EXISTS student(id INT, first_name TEXT, last_name TEXT)`

# Step 1: index.js

after the line `db.run(dbCommand)`:

![image](https://hackmd.io/_uploads/rk-5JAM_el.png)

# Step 2: index.js

at the bottom of `index.js`

![image](https://hackmd.io/_uploads/SJMze0Gugg.png)

# Step 3: index.js
replace lines #12 to #15 with:

```
app.route('/students/:id')
  .get((req, res) => {

  })
  .post((req, res) => {

  })
  .put((req, res) => {

  })
  .delete((req, res) => {

  });
```

# Step 4: post handler

```
.post((req, res) => {
    db.serialize(() => {
      db.run(
        'INSERT INTO student(id, first_name, last_name) VALUES(?, ?, ?)',
        [req.params.id, req.body.first_name, req.body.last_name],
        (err) => {
          if (err) return console.error(err.message);
          console.log('New student has been added.');
          res.send(`New student has been added: ${req.params.id} - ${req.body.first_name} ${req.body.last_name}`);
        }
      )
    });
  })
```

# Step 5: get handler

```
.get((req, res) => {
    db.serialize(() => {
      db.get(
        'SELECT id, first_name, last_name FROM student WHERE id = ?',
        [req.params.id],
        (err, row) => {
          if (err) return console.error(`Error encountered while querying db: ${err.message}`);

          if (row) {
            res.json({
              id: row.id,
              first_name: row.first_name,
              last_name: row.last_name
            });
          } else {
            res.send('Student not found', 404);
          }
        }
      )
    });
  })
```

# Step 6: put handler

```
.put((req, res) => {
    db.serialize(() => {
      db.run(
        'UPDATE student SET first_name = ?, last_name = ? WHERE id = ? ',
        [req.body.first_name, req.body.last_name, req.params.id],
        (err) => {
          if (err) return console.error(err.message);
          console.log('Student updated successfully!');
          res.send(`Student ${req.params.id} updated!`);
        }
      );
    });
  })
```

# Step 7: delete handler

```
.delete((req, res) => {
    db.serialize(() => {
      db.run(
        'DELETE FROM student WHERE id = ?',
        [req.params.id],
        (err) => {
          if (err) return console.error(err.message);
          console.log('Student deleted successfully!');
          res.status(204);
        }
      );
    });
  });
```

# Step 8: index.js

Move this line:

`app.use(express.json())`

before `app.route()...`

# Step 9: package.json

![image](https://hackmd.io/_uploads/rJHXO0f_el.png)

don't forget to include the "," at the end of line #7

# Step 10: start the server, from command prompt

`npm run start:dev`


## BUG!

find this line:

`res.status(204);`

and change it to:

`res.status(204).send();`
