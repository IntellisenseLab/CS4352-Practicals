# Hands on activity

## Theory

Following command,

```sh
tf.transformations.quaternion_from_euler(a, b, c, 'rxyz')
```

used in the server.py accepts 3 angles (radian values) which are in the order 'xyz'.

- 'a' correseponds to the angle around 'x',
- 'b' correseponds to the angle around 'y',
- 'c' correseponds to the angle around 'z',

you can change the 'rxyz' to any valid 3 angle representation (keeping r and prefix) and get the quarternion related to that transformation. As an example, In

```sh
tf.transformations.quaternion_from_euler(a, b, c, 'ryzx')
```

- 'a' correseponds to the angle around 'y',
- 'b' correseponds to the angle around 'z',
- 'c' correseponds to the angle around 'x',

<br>

## Exercise

First complete all the steps upto now and make sure the system works correctly. Then modify the client.py and calculate respective quaternions for the following angles which are given in the radians and are in the format <a, b, c, format>. 

0.00, 0.00, 0.00, xyz \
1.57, 1.57, 1.57, xyz

1.57, 0.00, 0.00, xyz \
0.00, 1.57, 0.00, xyz \
0.00, 0.00, 1.57, xyz 

3.14, 0.00, 0.00, xyz \
0.00, 3.14, 0.00, xyz \
0.00, 0.00, 3.14, xyz 

-1.57, 0.00, 0.00, xyz \
0.00, -1.57, 0.00, xyz \
0.00, 0.00, -1.57, xyz

1.57, 1.57, 0.00, xyz \
1.57, 0.00, 1.57, xyz \
0.00, 1.57, 1.57, xyz

1.57, 1.57, 0.00, yxz \
1.57, 0.00, 1.57, yxz \
0.00, 1.57, 1.57, yxz 

1.57, 1.57, 0.00, zyx \
1.57, 0.00, 1.57, zyx \
0.00, 1.57, 1.57, zyx 

# Submit a pdf named lab2_<index>.pdf at the end of the practical 

