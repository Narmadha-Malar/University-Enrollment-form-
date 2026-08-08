# University-Enrollment-form-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Campus Enrollment Form</title>
<style>
  body { font-family: 'Segoe UI', Arial, sans-serif; background-color: #eaf6f6; margin: 0; padding: 20px; }
  .container { max-width: 700px; margin: 0 auto; background-color: #ffffff; padding: 20px 30px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.15); border-top: 6px solid #16a085; }
  h1 { text-align: center; color: #117a65; }
  label { display: block; margin-top: 12px; font-weight: bold; color: #333; }
  input, select { width: 100%; padding: 8px; margin-top: 5px; border: 1px solid #b2d8d8; border-radius: 5px; font-size: 14px; background-color: #f7fdfd; }
  input:focus, select:focus { outline: none; border-color: #16a085; }
  button { margin-top: 20px; padding: 10px 20px; background-color: #16a085; color: white; border: none; border-radius: 5px; font-size: 15px; cursor: pointer; }
  button:hover { background-color: #138d75; }
  table { width: 100%; border-collapse: collapse; margin-top: 30px; }
  table, th, td { border: 1px solid #b2d8d8; }
  th, td { padding: 8px; text-align: left; font-size: 14px; }
  th { background-color: #16a085; color: white; }
  tr:nth-child(even) { background-color: #f2fbfa; }
  .delete-btn { background-color: #e74c3c; padding: 5px 10px; font-size: 12px; }
  .delete-btn:hover { background-color: #c0392b; }
  .empty-msg { text-align: center; color: #888; margin-top: 15px; }
</style>
</head>
<body>
<div class="container">
  <h1>Campus Enrollment Form</h1>
  <form id="enrollmentForm">
    <label for="name">Full Name</label>
    <input type="text" id="name" required>
    <label for="rollNo">Roll Number</label>
    <input type="text" id="rollNo" required>
    <label for="department">Department</label>
    <select id="department" required>
      <option value="">-- Select Department --</option>
      <option>Computer Science</option>
      <option>Mechanical</option>
      <option>Electrical</option>
      <option>Civil</option>
      <option>Business Administration</option>
    </select>
    <label for="year">Year</label>
    <select id="year" required>
      <option value="">-- Select Year --</option>
      <option>1st Year</option>
      <option>2nd Year</option>
      <option>3rd Year</option>
      <option>4th Year</option>
    </select>
    <label for="email">Email</label>
    <input type="email" id="email" required>
    <label for="phone">Phone Number</label>
    <input type="tel" id="phone" required>
    <button type="submit">Add Student</button>
  </form>
  <table id="studentTable">
    <thead>
      <tr>
        <th>Name</th><th>Roll No</th><th>Department</th><th>Year</th><th>Email</th><th>Phone</th><th>Action</th>
      </tr>
    </thead>
    <tbody id="tableBody"></tbody>
  </table>
  <p class="empty-msg" id="emptyMsg">No students added yet.</p>
</div>
<script>
  var students = [];
  var form = document.getElementById("enrollmentForm");
  var tableBody = document.getElementById("tableBody");
  var emptyMsg = document.getElementById("emptyMsg");
  form.addEventListener("submit", function (e) {
    e.preventDefault();
    var name = document.getElementById("name").value;
    var rollNo = document.getElementById("rollNo").value;
    var department = document.getElementById("department").value;
    var year = document.getElementById("year").value;
    var email = document.getElementById("email").value;
    var phone = document.getElementById("phone").value;
    var student = { name: name, rollNo: rollNo, department: department, year: year, email: email, phone: phone };
    students.push(student);
    displayStudents();
    form.reset();
  });
  function displayStudents() {
    tableBody.innerHTML = "";
    emptyMsg.style.display = students.length === 0 ? "block" : "none";
    for (var i = 0; i < students.length; i++) {
      var s = students[i];
      var row = document.createElement("tr");
      row.innerHTML = "<td>" + s.name + "</td><td>" + s.rollNo + "</td><td>" + s.department + "</td><td>" + s.year + "</td><td>" + s.email + "</td><td>" + s.phone + "</td><td><button class='delete-btn' onclick='deleteStudent(" + i + ")'>Delete</button></td>";
      tableBody.appendChild(row);
    }
  }
  function deleteStudent(index) {
    students.splice(index, 1);
    displayStudents();
  }
  displayStudents();
</script>
</body>
</html>
