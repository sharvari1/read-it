# read-it
signup.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="js/jquery-3.5.1.min.js"></script>
    <script src="signUp.js"></script>
    <title>Document</title>
</head>
<body>
    <form>
        Id:<input type="number" id="id">
        First Name:<input type="text" id="fName">
        Last Name :<input type="text" id="lName">
        Email :<input type="email" id="email">
        Password :<input type="password" id="password">
        <input type="submit" id="submit">
    </form>
       
    
</body>
</html>

signup.js

$('document').ready(()=>{
    $("#submit").click(()=>{
        console.log("posting");
        var id1=$("#id").val();
        console.log("id is"+id1);
        var FirstName1=$("#fName").val();
        var lastName1=$("#lName").val();
        var email1=$("#email").val();
        var password1=$("#password").val();
        $.ajax({
            url:"http://localhost:3000/User",
            method:"POST",
            data:{
                "id":id1,
                "first_name":FirstName1,
                "last_name": lastName1,
                "password":password1,
                "email": email1
            },
            success:(x)=>{
                alert(x.first_name+" name posted");
            },
            error:(e)=>{
                alert("error");
            }
        });
        })  
})

login.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="js/jquery-3.5.1.min.js"></script>
    <script src="logIn.js"></script>
    <title>Document</title>
</head>
<body>
    <form>
        Email :<input type="email" id="email">
        Password :<input type="password" id="password">
        <input type="button" id="submit" value="SUBMIT">
    </form>       
</body>
</html>

login.js
$('document').ready(()=>{
    $('#submit').click(()=>{
        var email1=$("#email").val();
        var password1=$("#password").val();
    $.ajax({
        url:"http://localhost:3000/User",
        method:"GET",
        success:(x)=>{
                        //console.log(x);
                        //console.log("length is"+x.length);
                        flag=1;
                        for(i=0;i<x.length;i++)
                        {
                            console.log("in for loop")
                            if(x[i].email===email1 && x[i].password===password1)
                            {
                                console.log("Login successful");
                                flag=0;
                                break;
                            }
                        }
                        if(flag)
                        {
                            console.log("login Failed");
                        }
                     },
        error : (e) =>{
                        console.log("Data Not Available");
                    }
             })
    })
})  
