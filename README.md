@@ -0,0 +1,98 @@
<html>

<head>
    <title>JSON Table</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
    <!-- <script src="get.js"></script> -->
    <style>
        #data1{
            margin-left: 20px;
    
        }
        #tr1{
            background-color: red;
            
        }
        td{
            
        }
    </style>
    <script>
        var p = document.querySelector("p");
        // var button=document.querySelector("button");



        // console.log("button click");
        var ajax = new XMLHttpRequest();
        ajax.open("GET", "http://dummy.restapiexample.com/api/v1/employees", true);
        ajax.send();

        ajax.onreadystatechange = function () {
            if (this.readyState == 4 && this.status == 200) {
                //  let a=this.responseText;
                console.log(this.responseText);
                // p.textContent=this.responseText;
                var serverData = JSON.parse(this.responseText);
                //  console.log(serverData);

                // var emp="<tr><td>ID</td><td>Name</td><td>Salary</td><td>Age</td></tr>";
                let data = ""
                for (let i of serverData.data) {

                    data += "<tr>"
                    data += "<td>" + i.id + "</td>"
                    data += "<td>" + i.employee_name + "</td>"
                    data += "<td>" + i.employee_salary + "</td>"
                    data += "<td>" + i.employee_age + "</td>"
                    data += "</tr>"

                    // emp= emp +"<tr>"+
                    // "<td>"+ i.id+"</td>"+
                    // "<td>"+i.employee_name+"</td>"+
                    // "<td>"+i.employee_salary+"</td>"+
                    // "<td>"+i.employee_age+"</td>"+
                    // "</tr>";
                    // console.log(i)
                    // console.log(i.id);
                    // console.log(i.employee_name);
                    // console.log(i.employee_salary);
                    // console.log(i.employee_age);
                }

                document.getElementById("data1").innerHTML += data;
                // table.innerHTML+=emp;

                //     var temp="<tr><th>Employee ID</th><th>Employee Name</th><th>Employee Salary</th><th>Employee Age</th></tr>";
                //     a.forEach((u)=>{
                //         temp=temp+"<tr>";
                //         temp=temp+"<td> "+u.id+" </td>";
                //         temp=temp+"<td> "+u.employee_name+" </td>"; 
                //         temp=temp+"<td> "+u.employee_salary+" </td>";
                //         temp=temp+"<td> " +u.employee_age+" </td></tr>";
                //     });
                //     //document.getElementById("data").innerHTML=temp;
                //     $("#data1").append(temp);

            }
        }

    </script>
</head>

<body>
    <h3>Presenting Data From Rest APIs</h3>
    <!-- <p id="data"></p> -->
    <table id="data1" border="1">
        <tr id="tr1">
            <td>ID</td>
            <td>Name</td>
            <td>Salary</td>
            <td>Age</td>
        </tr>

    </table>
    <!-- <button id="load">Click To View</button> -->
</body>

</html>
