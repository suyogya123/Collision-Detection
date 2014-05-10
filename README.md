Collision-Detection
===================

Collision detection is one of the technique of determining when and how two objects basically collide. It has many application in today’s world including in Air traffic controls, to where the planes are projected if it flies with certain initial conditions. Today in my post, by using Vpython, I am trying to show two different ways of detecting collisions of two balls, which are spheres.  
Let me start up with the first way I tried to approach this question. Basically at first all of my initial conditions are given that is my initial x& y position of both the ball and also the velocity in x and y direction of both the sphere. As you can see in the code ball1, ball2, ball1.velocity, ball2.velocity.Then I calculated the distance between the centers of both the sphere. I used a function called def dis in my code. Whenever the def dis comes up it returns the distance between the two balls’ started with time t = 0 and iterate it with an addition of 0.05 in each iteration. That would just update my position of both the sphere as the time increases. So if you really are looking for time for collisions of the two balls you must be lucky in increasing the time, and make the increment in time very less. It is so because, in one moment the balls might not collide and the next iteration they might cross each other. It is so because, after each iteration of time, it measures the distance between the two balls and checks if it is less than or equal to the radius between the two balls, as in the code  

    if dis(ball1, ball2)<=ball1.radius+ball2.radius:
If the condition is correct, it print out the balls collide and the time required as t.

Here is the 1st method

![snapshots](https://raw.githubusercontent.com/suyogya123/Collision-Detection/master/Snapshots/First%20Method.jpg)

The code was alright until my dt was very small, because as I make my dt very large like 5, the program does not be quite accurate. So I tried it in a different way, which is more accurate in detecting the collisions between two spheres, without iterating time. 
The second way I approached the problem was by first mathematically solving the equation for the position as I update it. That checks if both the balls, actually collides before the next step. Below is the technique that I used
Let us suppose the initial positions of the balls be (x01, y01) and (x02, y02) of the ball1 and ball2. As you can see in the code,

    ball1 = sphere (pos= (-5, 0, 0), radius=0.2, color=color.red)
    ball2 = sphere (pos= (5, 0,0), radius = 0.5, color= color.cyan)
 
Similarly let (Vx1 Vy1) and (Vx2, Vy2) be the velocity in x and y direction of the first and and second 

    ball1.velocity = vector (0.1,0.1,0)
    ball2.velocity= vector(-0.1,0.1,0)
The idea is the same as above in the first method, the two balls collide if the distance between the two is less than or equal to its radius. So I calculated total radius

     R = ball1.radius+ball2.radius
Now with the all initial condition of both the balls given, I used kinematic equation to solve for the unknown time ‘t’.
 Using kinematic equation,
 
    X1 =X01+Vx1*t
    Y1 =Y01+Vy1*t
    X2 =X02+Vx2*t
    Y2 =Y02+Vy2*t
So then after time t , distance between the both the ball can be calculated from distance formula,

    ((X2-X1) **2+ (Y2-Y1) **)**0.5 
 So using the condition of distance between them equal to the total radius, the only unknown ‘t’ can be calculated
 
    ((X2-X1) **2+ (Y2-Y1) **) = R**2
Then plugging back the kinematic equation for each of them as mentioned above, we get a quadratic equation of this form

    (dx)^2+(dy)^^2 – R^2+ (2*dx*vdx+2*dy*vdy)* t+((vdx)^2+(vdy)^2)*t^2 =0
     Where, dx = X02 –X01 
    	 dy = Y02-Y01
    	 vdx =Vx2-Vx1
    	 vdy = Vy2 –Vy1 
As you can see in the code

    dx = ball2.pos.x-ball1.pos.x
    dy = ball2.pos.y-ball1.pos.y
    vdx = ball2.velocity.x-ball1.velocity.x
    vdy = ball2.velocity.y-ball1.velocity.y
 Now comparing the quadratic equation we have 


    Where ,a = (vdx)^2 – (vdy)^2
    	b = 2*(dx*vdx+dy*vdy)
    	c = (rdx)^2 +(rdy)^2 –R^2
    	
So by using  

    t = (-b+((b^2)-(4*a*c)))/2*a  or t = (-b-((b^2)-(4*a*c)))/2*a
If time t is positive, they collide at that time. If‘t’ is undefined than the two balls don’t collide. And if, negative it indicates they collided in past at that time. You might get two times, as‘t’ was in quadratic form in above equation. Just take the one which is less because we really don’t care about the second one, as they change the path after collision.
 So here’s the second way.   
![snapshots](https://raw.githubusercontent.com/suyogya123/Collision-Detection/master/Snapshots/Second%20Method.JPG)


The fun part was that with the same initial conditions, both my codes works and give me the same time. But, in the first code I was lucky as I took a very small increment in time. If I used time’s increment bigger definitely I wouldn’t have been able to determine my collision. So for detection of collision definitely the second approach is better.

##This was my approach to detect collisions of two spheres. If you have new ideas , or you want to add anyhting to my code Please feel free to fork the project and contribute.Thank You!

