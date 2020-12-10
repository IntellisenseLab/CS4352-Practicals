#!/usr/bin/env python

from __future__ import print_function

from lab_2_3dPose.srv import angles,anglesResponse
import rospy
import tf

def convert (a, b, c, format):
    return tf.transformations.quaternion_from_euler(a, b, c, 'r'+format)

def handle_euler(req):
    print("Recieved [%s, %s, %s, %s]" %(req.a, req.b, req.c, req.format))

    result = convert(req.a, req.b, req.c, req.format)
    
    response = anglesResponse()

    response.qx = result[0]
    response.qy = result[1]
    response.qz = result[2]
    response.qw = result[3]

    print("Returning [%s, %s, %s, %s]" %(response.qx, response.qy, response.qz, response.qw))
    
    return response

def euler_to_quarternion_server():
    rospy.init_node('euler_to_quarternion_server')
    s = rospy.Service('euler_to_quarternion', angles, handle_euler)
    print("Ready to convert.")
    rospy.spin()

if __name__ == "__main__":
    euler_to_quarternion_server()