<!DOCTYPE html>
<html>
<head>
  <title>User List</title>
  <style>  
    body {
      font-family: Arial, sans-serif;
    }
    .user-card {
      border: 1px solid #ccc;
      padding: 10px;
      margin: 10px;
      border-radius: 8px;
    }
  </style>
</head>
<body>
  <h2>User List</h2>
  <div id="userList">Loading users...</div>

  <script>
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(response => response.json()) // Parse JSON
      .then(users => {
        const userList = document.getElementById('userList');
        userList.innerHTML = '';

        users.forEach(user => {
          const userCard = document.createElement('div');
          userCard.className = 'user-card';
          userCard.innerHTML = `<strong>${user.name}</strong><br>Email: ${user.email}`;
          userList.appendChild(userCard);
        });
      })
      .catch(error => {
        console.error('Error fetching users:', error);
        document.getElementById('userList').textContent = 'Failed to load users.';
      });
  </script>
</body>
</html># UserList
