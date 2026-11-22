# ui-lab

Automated UI testing lab (ITDS362). I chose two tool parts: Robot Framework (Part 3) and Cypress (Part 4).

## robot/
Robot Framework tests with SeleniumLibrary for the Selenium web form and for test case QP-01 on QuickPizza. Run the tests from the robot folder with the virtual environment active:

    robot pizza_scenario.robot

## cypress/
Cypress tests for the Selenium web form and for test case QP-01 on QuickPizza. Run the tests from the cypress folder:

    npx cypress run