Q1>Responsive Multi-Column Form with Flexbox by Using HTML and CSS
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        body{
            font-family: sans-serif;
            margin:20px;
            background:#f8f8f8;
        }

        form{
            background:#fff;
            padding:20px;
            border-radius:8px;
            max-width:800px;
            margin:auto;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        fieldset{
            border:name;
            padding:0;
            margin:0 0 20px 0;
        }

        legend{
            font-size:1.2em;
            font-weight:bold;
            margin-bottom:10px;
        }
        .form-row{
            display:flex;
            flex-wrap:wrap;
            gap:20px;
        }
        .form-group{
            flex:1 1 300px;
            display:flex;
            flex-direction:column;
        }
        label{
            margin-bottom:6px;
            font-weight:500;
        }
        input,select,textarea{
            padding:8px;
            border:1px solid #ccc;
            border-radius:4px;
            font-size:1em;
        }
        .error{
            color:red;
            font-size:0.9em;
            margin-top:4px;
        }
        @media (max-width:600px){
            .form-row{
                flex-direction:column;
            }
        }
        button{
            padding:10px 20px;
            font-size:1em;
            background-color:#007bff;
            border:none;
            color:white;
            border-radius:4px;
            cursor:pointer;
        }
        button:hover{
            background-color:#0056b3;
        }

    </style>
</head>
<body>
    <form>
        <filedset>
            <legend>Personal Information</legend>
            <div class="form-row">
                <div class="form-group">
                    <label for="fname">First Name</label>
                    <input type="text" id="fname" rqeuired />
                    <div class="error">First name is required.</div>
                </div>
                <div class="form-group">
                    <label for="lname">Last name</label>
                    <input type="text" id="lname" name="lname" />
                </div>
            </div>
        </filedset>

        <filedset>
            <legend>Contact Details</legend>
            <div class="form-row">
                <div class="form-group">
                    <label for="email">Email</label>
                    <input type="email" id="email" name="email" />
                </div>
                <div class="form-group">
                    <label for="phone">Phone Number</label>
                    <input type="tel" id="phone" name="phone" />
                </div>
            </div>
        </filedset>

        <button type="submit">Submit</button>
    </form>
    
</body>
</html>

#Q2)Responsive Hamburger Menu.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS-Only Hamburger Menu</title>
    <link rel="stylesheet" href="hamburgerMenu.css">
</head>
<body>
    <!--Hidden checkbox to toggle the menu-->
    <input type="checkbox" id="menu-toggle" />
    <label class="menu-btn" for="menu-toggle">
        <span></span>
    </label>  
    
    <!--Slide-in full screen menu-->
    <nav class="menu">
        <a href="#">Home</a>
        <a href="#">About</a>
        <a href="#">Services</a>
        <a href="#">Contact</a>
    </nav>
</body>
</html>

Css:-
*{
    box-sizing:border-box;
}
body{
    margin:0;
    font-family:sans-serif;
}
/hide checkbox/
#menu-toggle{
    display:none;
}
/Hamburger Icon/
.menu-btn{
    position:fixed;
    top:20px;
    right:20px;
    width:30px;
    height:22px;
    cursor:pointer;
    z-index:999;
}
.menu-btn span,
.menu-btn::before,
.menu-btn::after{
      content:' ';
      position:absolute;
      height:4px;
      width:100%;
      background:#333;
      transition:all 0.4s ease;
      border-radius:2px;
}
.menu-btn span{
    top: 9px;
}
.menu-btn::before{
    top:0;
}
.menu-btn::after{
    bottom:0;
}
/transform into X when checked/
#menu-toggle:checked + .menu-btn::before{
    transform:rotate(45deg);
    top:9px;
}
#menu-toggle:checked + .menu-btn::after{
    transform:rotate(-45deg);
    bottom:9px;
}
#menu-toggle:checked + .menu-btn span{
    opacity:0;
}
/Slide-in menu styles/
.menu{
    position:fixed;
    top:0;
    right:-100%;
    width:100%;
    height:100vh;
    background: #111;
    color:white;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    transition:right 0.5s ease;
    z-index:998;
}
#menu-toggle:checked ~ .menu{
    right:0;
}
.menu a{
    color:white;
    text-decoration:none;
    font-size:2rem;
    margin:1rem 0;
    transition:color 0.3s ease;
}
.menu a:hover{
    color:#f90;
}

#Q3)Profile Settings Menu
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Custom Form Elements</title>
    <link rel="stylesheet" href="profileSetting.css">
</head>
<body>
    <div class="form-container">
        <h2>Profile Settings</h2>
        <form>
            <!--Custom Dropdown-->
            <label for="country">Select Country</label>
            <div class="Custom-select-wrapper">
                <select id="country" name="country">
                    <option value="">Choose a country</option>
                    <option value="india">India</option>
                    <option value="usa">USA</option>
                    <option value="germany">Germany</option>
                    <option value="japan">Japan</option>
                </select>
            </div>

            <!--Custom Checkbox-->
            <label>Skills</label>
            <div class="checkbox-group">
                <label class="custom-checkbox">
                    <input type="checkbox" name="skills" value="html">
                    <span>HTML</span>
                </label>
                <label class="custom-checkbox">
                    <input type="checkbox" name="skills" value="css">
                    <span>CSS</span>
                </label>
                <label class="custom-checkbox">
                    <input type="checkbox" name="skills" value="js">
                    <span>JavaScript</span>
                </label>
            </div>

            <!--Custom Radio Button-->
            <label>Gender</label>
            <div class="radio-group">
                <label class="custom-radio">
                    <input type="radio" name="gender" value="male">
                    <span>Male</span>
                </label>
                <label class="custom-radio">
                    <input type="radio" name="gender" value="female">
                    <span>Female</span>
                </label>
                <label class="custom-radio">
                    <input type="radio" name="gender" value="other">
                    <span>Other</span>
                </label>
            </div>
            <button type="submit">Submit</button>
        </form>
    </div>
</body>
</html>
Css:-
body{
    font-family:Arial, sans-serif;
    background:#f5f5f5;
    padding:40px;
}

.form-container{
    background:white;
    max-width:400px;
    margin:auto;
    padding:30px;
    border-radius:10px;
    box-shadow:0 0 15px rgba(0,0,0,0.1);
}
h2{
    text-align:center;
    margin-bottom:20px;
}
label{
    display:block;
    margin:15px 0 5px;
    font-weight:bold;
}
select{
    width:100%;
    padding:10px;
    border-radius:8px;
    border:1px solid #ccc;
    appearance: none;
    background:url('data:image/svg+xml;');
    background-size:15px;
}
.custom-checkbox,
.custom-radio{
    display:flex;
    align-items:center;
    margin:5px 0;
    position:relative;
}
.custom-checkbox input,
.custom-radio input{
    appearance:none;
    width:18px;
    height:18px;
    border:2px solid #666;
    border-radius:4px;
    margin-right:10px;
    cursor:pointer;
    position:relative;
}
.custom-radio input{
    border-radius:50%;
}
.custom-checkbox input:checked{
    background-color:#4CAF50;
    border-color:#4CAF50;
}
.custom-radio input:checked{
    background-color:#2196F3;
    border-color:#2196F3;
}
.custom-checkbox input:checked::after{
   content:"✓";
   color:white;
   font-size:14px;
   position:absolute;
   left:3px;
   top:-1px;
}
.custom-radio input:checked::after{
    content:"";
    width:8px;
    height:8px;
    background:white;
    border-radius:50%;
    position:absolute;
    left:5px;
    top:5px;
}
button{
    width:100%;
    padding:12px;
    margin-top:20px;
    background-color:#333;
    color:white;
    border:none;
    border-radius:8px;
    cursor:pointer;
}
button:hover{
    background-color:#555;
}

#Q4)Min Max attributes in HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>The Input min and max attributes</h1>

    <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Ad porro et nostrum hic esse perspiciatis eum modi distinctio culpa fuga perferendis quo eaque enim aspernatur totam deleniti cum, asperiores facere?</p>

    <form action="/action_page.php">
        <label for="datemax">Enter a date before 1980-01-01:</label>
        <input type="date" id="datemax" name="datemax" max="1979-12-31"><br><br>

        <label for="datemin">Enter a date after 2000-01-01:</label>
        <input type="date" id="datemin" name="datemin" min="2000-01-02"><br><br>

        <label for="quantity">Quantity(between 1 and 5):</label>
        <input type="number" id="quantity" name="quantity" min="1" max="5"><br><br>

        <input type="submit" value="Submit">
    </form>
</body>
</html>

#Q5)Traffic Light Signal by html and css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="trafficlight.css">
</head>
<body>
    <div class="light">
        <div class="trafficlight">
            <div class="red"></div>
            <div class="yellow"></div>
            <div class="green"></div>
        </div>
    </div>
</body>
</html>
CSS:-
 .red{
    display:flex;
    background-color:red;
    height:50px;
    width:50px;
    align-items:center;
    border-radius:50%;
    margin:15px 10px;
    box-shadow:2px 1px 15px red;
}
.yellow{
    display:flex;
    background-color:rgb(255,228,26);
    height:50px;
    width:50px;
    border-radius:50%;
    margin:15px 10px;
    box-shadow:2px 1px 15px rgb(231,215,26)
}
.green{
    display:flex;
    background-color:rgb(41,201,49);
    height:50px;
    width:50px;
    border-radius:50%;
    margin: 15px 10px;
    box-shadow:2px 1px 15px rgb(62,236,36);
}
h1{
    text-align:center;
    align-items:center;
    display:flex;
}
body{
    display:flex;
    justify-content:center;
    align-items:center;
}
.trafficlight{
    background-color:black;
    border-radius:10px;
}

#Q6)Complex Table by html and css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Complex Table</title>
    <link rel="stylesheet" href="ComplexTable.css">
</head>
<body>
    <div class="table-container">
        <table>
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Full Name</th>
                    <th>Email</th>
                    <th>Department</th>
                    <th>Join Date</th>
                    <th>Status</th>
                </tr>
            </thead>
            <tbody>
                <!--Repeat rows for demonstrater-->
                <tr>
                    <td>001</td>
                    <td>John Doe</td>
                    <td>john@example.com</td>
                    <td>Enginnering</td>
                    <td>2021-05-15</td>
                    <td>Active</td>
                </tr>
                <tr>
                    <td>002</td>
                    <td>Jane Smith</td>
                    <td>jane@example.com</td>
                    <td>Marketing</td>
                    <td>2020-11-21</td>
                    <td>Inactive</td>
                </tr>
            </tbody>
        </table>
    </div>
    
</body>
</html>
Css:-
body{
    font-family:Arial,sans-serif;
    margin:20px;
    background:#f4f4f4;
}
.table-container{
    overflow-x:auto;
    max-width:100%;
    background:white;
    border:1px solid #ddd;
    border-radius:6px;
}
table{
    width:100%;
    border-collapse:collapse;
    min-width:800px;
}
thead{
    background:#333;
    color:white;
    position:sticky;
    top:0;
    z-index:2;
}
thead th{
    padding:12px;
    text-align:left;
    background:#333;
}
tbody td{
    padding:12px;
    border-bottom:1px solid #ccc;
}
tbody tr:nth-child(even){
    background-color:#f9f9f9;
}
tbody tr:nth-child(odd){
    background-color:#fff;
}
@media screen and (max-width:768px){
    table{
        font-size:14px;
    }
    thead th, tbody td{
        padding:10px;
    }
}

#Q7)Real World Senario E-commerce Drop down menu
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shop Dropdown</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <nav class="menu">
        <ul>
            <li><a href="#">Home</a></li>

            <li class="has-submenu">
                <input type="checkbox" id="shop-toggle">
                <label for="shop-toggle">Shop</label>
                <ul class="submenu">
                <li><a href="#">All Products</a></li>

                <li class="has-submenu">
                <input type="checkbox" id="men-toggle">
                <label for="men-toggle">Men</label>
                <ul class="submenu">
                    <li><a href="#">Shirts</a></li>
                    <li><a href="#">Shoes</a></li>
                    <li><a href="#">Accessories</a></li>
                </ul>
                </li>
                

                <li class="has-submenu">
                    <input type="checkbox" id="women-toggle">
                    <label for="women-toggle">Women</label>
                    <ul class="submenu">
                        <li><a href="#">Dresses</a></li>
                        <li><a href="#">Handbags</a></li>
                        <li><a href="#">Jewelry</a></li>
                    </ul>
                </li>
            </li>
                </ul>
            </li>

            <li><a href="#">About Us</a></li>
            <li><a href="#">Contact</a></li>
        </ul>
    </nav>
    
</body>
</html>
Css:-
body{
   font-family:'Segoe UI', sans-serif;
   background:#f8f9fa;
   padding:30px;
}

.menu ul{
    list-style:none;
    margin:0;
    padding:0;
    background:#212529;
    width:250px;
    border-radius:6px;
    overflow:hidden;
}

.menu li{
    position:relative;
}

.menu a,
.menu label{
    display:block;
    color:#f1f1f1;
    text-decoration:None;
    padding:14px 20px;
    cursor:pointer;
    transition:background 0.3s ease;
}

.menu a:hover,
.menu label:hover{
    background:#343a40;
}

input[type="checkbox"]{
    display:none;
}

.submenu{
    max-height:0;
    overflow:hidden;
    background:#343a40;
    transition: max-height 0.4s ease-in-out;
}
.has-submenu input:checked + label +.submenu{
    max-height:500px;
}

.submenu a{
    padding-left:40px;
    background:#3e444a;
}

.submenu .submenu a{
    padding-left:60px;
    background:#495057;
}

#Q8)Bulid a tabbed navigation system that switches contents on click using only css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Real Estate Property Tabs</title>
    <link rel="stylesheet" href="tabbedNavigationsystem.css">
</head>
<body>
    <div class="tabs-container">
        <!--Tab Nevigation-->
        <input type="radio" id="tab1" name="tabs" checked>
        <input type="radio" id="tab2" name="tabs">
        <input type="radio" id="tab3" name="tabs">

        <!--Tab labels-->
        <label for="tab1" class="tab-label">Property Details</label>
        <label for="tab2" class="tab-label">Photo</label>
        <label for="tab3" class="tab-label">Contact Info</label>

        <!--Tab Content-->
        <div class="tab-content" id="content1">
            <h2>Property Details</h2>
            <p><strong>Address:</Address></strong>1234 Elm Street,Springfield,IL</p>
            <p><strong>Price:</strong>$350,000</p>
            <p><strong>Size</strong>2,500 sqft</p>
            <p><strong>Bedrooms:</strong>4</p>
            <p><strong>Bathroom:</strong>3</p>
            <p><strong>Year Built:</strong>2015</p>
            <p><strong>Description:</strong>A beautiful modern home with spacious interior efficient features</p>
        </div>
        <div class="tab-content" id="content2">
            <h2>Photos</h2>
            <div class="photo-gallary">
                <img src="image.jpg" alt="Front">
                <img src="image1.jpeg" alt="Bedroom">
                <img src="image2.jpeg" alt="Hall">
                <img src="image4.jpeg" alt="Bedroom">
            </div>
        </div>
        <div class="tab-content" id="content3">
            <h2>Contact Info</h2>
            <p><strong>Agent Name:</strong>John Doe</p>
            <p><strong>Email:</strong>john.doe@example.com</p>
            <p><strong>Phone:</strong>(91+)12345667</p>
            <p><strong>Office Hours:</strong>Mon-Fri:9:00AM - 5:00PM</p>
        </div>
    </div>
    
</body>
</html>
Css:-
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}
body{
    font-family:Arial,sans-serif;
    background-color:#f4f4f4;
    padding:20px;
}
.tab-container{
    width:100%;
    max-width:900px;
    margin:0 auto;
    border:1px solid #ddd;
    border-radius:8px;
    background-color:#fff;
}
input[type="radio"]{
    display:none;
}
.tab-label{
    display:inline-block;
    padding:15px;
    text-align:center;
    background-color:#f4f4f4;
    border:1px solid #ddd;
    cursor:pointer;
    transition:background-color 0.3s ease, color blue;
}
.tab-label:hover{
    background-color:#ddd;
}
.tab-label:active{
    background-color:#bbb;
}

.tab-content{
    display:none;
    padding:20px;
    background-color:#fff;
    border-top:1px solid #ddd;
}
input#tab1:checked~.tab-content#content1,
input#tab2:checked~.tab-content#content2,
input#tab3:checked~.tab-content#content3{
    display:block;
}
input#tab1:checked~.tab-label[for="tab1"],
input#tab2:checked~.tab-label[for="tab2"],
input#tab3:checked~.tab-label[for="tab3"]{
    background-color:#007BFF;
    color:#fff;
}
.photo-gallary{
    display:grid;
    grid-template-columns:repeat(auto-fill,minmax());
    gap:10px;
    
}
.photo-gallary img{
    width:100%;
    height:auto;
    border-radius:8px;
    box-shadow:0 2px 4px rgba(0,0,0,0.1);
}

#Q9)Glassmorphic card design
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Glassmorphism Card</title>
    <link rel="stylesheet" href="GlassmorphicCardDesign.css" />
</head>
<body>
    <div class="background">
        <div class="glass-card">
            <img src="image5.jpg" width="100" height="100" class="profile-img">
            <h2>Louis Johnson</h2>
            <p>UI/UX Designer</p>
            <button>Follow</button>
        </div>
    </div>
    
</body>
</html>
Css:-
body,html{
    height:100%;
    margin:0;
    font-family:'Segoe UI',sans-serif;
}
.background{
    height:100%;
    display:flex;
    justify-content:center;
    align-items:center;
    background:linear-gradient(135deg, #ff7eb3,rgba(20, 167, 167, 0.933))
}
.glass-card{
    width:280px;
    padding:30px;
    border-radius:20px;
    background:rgba(255,255,255,0.1);
    box-shadow:0 8px 32px rgba(0,0,0,0.25);
    backdrop-filter:blur(12px);
    -webkit-backdrop-filter:blur(12px);
    border:1px solid rgba(255,255,255,0.2);
    text-align:center;
    color:#fff;
}
.profile-img{
    width:100px;
    height:100px;
    border-radius:50%;
    border:3px solid rgba(255,255,255,0.3);
    margin-bottom:15px;
}
.glass-card h2{
    margin:10px 0 5px;
    font-size:22px;
}
.glass-card p{
    margin-bottom:20px;
    font-size:16px;
    color:#e0e0e0;
}
.glass-card button{
    padding:10px 20px;
    border:none;
    border-radius:25px;
    background-color:rgba(255,255,255,0.3);
    color:#6c2f2f;
    cursor:pointer;
    transition:background-color 0.3s;
}
.glass-card button:hover{
    background-color:rgba(255,255,255,0.5);
}

#Q10)Css Scroll snap
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Scroll Snap Gallary</title>
    <link rel="stylesheet" href="CssScrollSnap.css">
</head>
<body>
    <h2>Featured Products</h2>

    <div class="scroll-container">
        <div class="card">
            <img class="product-img" src="image9.jpeg">
            <div class="product-info">
                <h3>Stylish Sneakers</h3>
                <p>$59.99</p>
            </div>
        </div>
        <div class="card">
            <img class="product-img" src="image6.jpeg">
            <div class="product-info">
                <h3>Luxury Watch</h3>
                <p>$149.99</p>
            </div>
        </div>
        <div clas="card">
            <img class="product-img" src="image7.jpeg">
            <div class="product-info">
                <h3>Wireless Headphones</h3>
                <p>$89.99</p>
            </div>
        </div>
        <div class="card">
            <img class="product-img" src="image8.jpeg">
            <div class="product-info">
                <h3>Powerful Laptop</h3>
                <p>$999.99</p>
            </div>
        </div>
    </div>
</body>
</html>
Css:-
body{
    margin:0;
    font-family:Arial,sans-serif;
    background:#f8f8f8;
}
h2{
    text-align:center;
    padding:1rem;
}
.scroll-container{
    display:flex;
    overflow-x:auto;
    scroll-snap-type:x mandatory;
    scroll-padding:1rem;
    gap:1rem;
    padding:1rem;
}
.scroll-container::-webkit-scrollbar{
    display:none;
}
.card{
    flex:0 0 80%;
    background:white;
    border-radius:12px;
    padding:1rem;
    scroll-snap-align:center;
    box-shadow:0 4px 10px rgba(0,0,0,0.1);
    transition:transform 0.3s;
}
.card:hover{
    transform:scale(1.03);
}
.product-img{
    width:100%;
    height:180px;
    object-fit:cover;
    border-radius:10px;
}
.product-info{
    margin-top:1rem;
}
