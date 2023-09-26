#!/usr/bin/env python

import rospy
from home_inspection.srv import InspectHome, InspectHomeResponse

def inspect_home_server(request):
    # Perform home inspection tasks here
    response = InspectHomeResponse()
    response.inspect_home = True
    return response

if __name__ == '__main__':
    rospy.init_node('inspect_home_server')
    service = rospy.Service('inspect_home', InspectHome, inspect_home_server)
    rospy.spin()
