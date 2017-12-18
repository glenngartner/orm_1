# SQLite recipe

* Here's the full recipe I used to create the db:

  ```sql
  PRAGMA FOREIGN_KEYS = ON;

  CREATE TABLE user (
    id INTEGER PRIMARY KEY,
    firstName TEXT,
    lastName TEXT,
    username TEXT,
    age INTEGER,
    email TEXT
  );
  CREATE TABLE post (
    id INTEGER PRIMARY KEY,
    title TEXT,
    body TEXT,
    user_id INTEGER NOT NULL,
    FOREIGN KEY(user_id) REFERENCES user(id)
  );
  CREATE TABLE comment(
    id INTEGER PRIMARY KEY,
    body TEXT,
    post_id INTEGER NOT NULL,
    user_id INTEGER NOT NULL,
    FOREIGN KEY(post_id) REFERENCES post(id),
    FOREIGN KEY (user_id) REFERENCES user(id)
  );

  INSERT INTO user(firstName, lastName, username, age, email) VALUES ('glenn', 'gartner', 'ggartner', 35, 'g@gmail.com');
  INSERT INTO user(firstName, lastName, username, age, email) VALUES ('devon', 'gartner', 'devastator', 5, 'd@gmail.com');
  INSERT INTO user(firstName, lastName, username, age, email) VALUES ('thea', 'gartner', 'tbee', 3, 't@gmail.com');

  INSERT INTO post(title, body, user_id) VALUES ('Deep in the Heart of Texas', 'The stars at night are big and bright, Deep in the heart of Texas, The prairie sky is wide and high, Deep in the heart of Texas.', 1);
  INSERT INTO post (title, body, user_id) VALUES (
    'Follow the Drinkin'' Gourd',
    'When the sun goes down' ||
    'And the first quail call' ||
    'Follow the drinkin'' gourd' ||
    'Then it''s time, children' ||
    'to come one and all and' ||
    'Follow the drinkin'' gourd',
    2
  );

  INSERT INTO post(title, body, user_id) VALUES ('New Post', 'A short post', 3);
  INSERT INTO post(title, body, user_id) VALUES ('Another New Post', 'Shorter post', 1);
  INSERT INTO post(title, body, user_id) VALUES ('Final Post', 'From the post office', 2);
  INSERT INTO post(title, body, user_id) VALUES ('Whining', 'Daddy, I WANT SOME WATER!!', 2);

  INSERT INTO comment (body, post_id, user_id) VALUES ('Follow the Drinking Gourd was published in 1928.', 2, 1);
  INSERT INTO comment (body, post_id, user_id) VALUES ('The Underground Railroad used the Drinking Gourd song to secretly communicate escape instructions and a map to slaves.', 2, 3);
  INSERT INTO comment (body, post_id, user_id) VALUES ('That''s a boring post', 3, 1);
  INSERT INTO comment (body, post_id, user_id) VALUES ('Riveting commentary!', 5, 3);
  INSERT INTO comment (body, post_id, user_id) VALUES ('Get your own water, like I taught you to.', 6, 1);
  ```
* Here's the pseudocode: 

  ```txt

  ```