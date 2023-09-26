#!/usr/bin/env python

import rospy
import actionlib
from home_inspection.msg import HomeInspectionAction, HomeInspectionFeedback, HomeInspectionResult

def home_inspection_server():
    rospy.init_node('home_inspection_server')
    server = actionlib.SimpleActionServer('home_inspection', HomeInspectionAction, execute_cb, False)
    server.start()
    rospy.spin()

def execute_cb(goal):
    # Perform home inspection tasks here
    # Provide feedback as needed
    feedback = HomeInspectionFeedback()
    feedback.feedback = "Inspection in progress..."
    server.publish_feedback(feedback)
    # Perform your inspection tasks
    # Populate the result message
    result = HomeInspectionResult()
    result.result = "Home inspection completed."
    server.set_succeeded(result)

if __name__ == '__main__':
    home_inspection_server()



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
