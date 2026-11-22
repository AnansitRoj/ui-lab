# UI lab results

Tool parts that I chose: Part 3 (Robot Framework) and Part 4 (Cypress)

## Part 0

* Step 0.1, Chrome version: 158.0.8127.37
* Step 0.3, ChromeDriver version: 158.0.8127.36
* Step 0.4, locator of Pizza, Please!: //button[normalize-space()='Pizza, Please!']
* Step 0.4, locator of Excluded tools: select[multiple]
* Step 0.4, locator of Must be vegetarian: //label[normalize-space()='Must be vegetarian']/preceding-sibling::input
* Step 0.4, locator of Custom Pizza Name: input#pizza-name
* Step 0.5, pizza name, tool and calories of the run by hand: Lab Pizza 20261122-212759, Pizza cutter, 550

| Step | Actual result | Pass or fail |
|------|---------------|--------------|
| 1 | The heading Looking to break out of your pizza routine? was shown | Pass |
| 2 | Max Calories per Slice, Excluded tools, Must be vegetarian and Custom Pizza Name appeared | Pass |
| 3 | Fields held 600, Knife excluded, vegetarian ticked and the name Lab Pizza 20261122-212759 | Pass |
| 4 | Answer showed the name Lab Pizza 20261122-212759, tool Pizza cutter and 550 calories per slice | Pass |
| 5 | The page said Please log in first. | Pass |
| 6 | After signing in as admin, the page showed Latest pizza recommendations | Pass |
| 7 | The list had the line Lab Pizza 20261122-212759 (tool=Pizza cutter, ingredients_number=6), the same tool as in step 4 | Pass |

## Part 3: Robot Framework

* robot --version: Robot Framework 7.5.1 (Python 3.14.0 on win32)
* Step 3.2, failure message for the wrong title: Title should have been 'Web Form' but was 'Web form'.
* Step 3.8, run 1, result, elapsed time and pizza name: Pass, 00:00:08.972, Lab Pizza 20261122-224107
* Step 3.8, run 2, result, elapsed time and pizza name: Pass, 00:00:09.276, Lab Pizza 20261122-224124

## Part 4: Cypress

* node --version, npm --version and npx cypress version: v22.21.0, 10.9.4, Cypress package version 16.3.0 (binary 16.3.0)
* Step 4.6, tool and calories in the answer of POST /api/pizza: Pizza cutter, 350
* Step 4.7, the line of the admin list that shows your pizza: Lab Pizza 20261123-011002 (tool=Pizza cutter, ingredients_number=5)
* Step 4.8, run 1, result, duration and pizza name: Pass, 00:00:12, name not recorded
* Step 4.8, run 2, result, duration and pizza name: Pass, 00:00:11, Lab Pizza 20261123-005738
* Step 4.9 (optional), browser and result: Not done

## Part B

1. The Max Calories per Slice input is located through its label because the page does not provide a stable id for this field. A tester can find the input by using the label text and its relationship with the input. The page could add an id such as max-calories-per-slice to the input. Then the test could use that id directly, making the locator clearer and easier to maintain.

2. This check is a consistency oracle because it compares the tool shown in the recommendation with the tool stored in the admin list. It can catch a fault where the admin page saves or displays a different tool from the one returned to the customer. In my Cypress test, the tool from the pizza response is saved and compared with the tool in the admin list.

3. The test could check that every ingredient in the recommended pizza is vegetarian. To do this, the page or API response should provide the ingredient list and reliable information about whether each ingredient is vegetarian. Another option is for the server to return a vegetarian status for the pizza. The test could then fail if the pizza contains a non-vegetarian ingredient.

4. Robot Framework uses SeleniumLibrary keywords such as Wait Until Element Contains and Wait Until Page Contains to wait for the expected page content. Cypress automatically retries commands and assertions until they pass or reach the timeout. Robot Framework uses readable keywords and a resource file, while Cypress uses JavaScript and custom commands; both took some setup to complete QP-01. Robot Framework provides detailed HTML logs and reports, while Cypress provides a clear command log, terminal results, screenshots and videos.

5. I would choose Cypress for the automated UI tests in Project 2. It automatically waits for elements and assertions, so I do not need to write many separate wait commands. It also provides screenshots and videos that make it easier to check what happened when a test fails.

6. In Robot Framework, I would change the locator inside the Fill In The Pizza Request keyword in resources/quickpizza.resource. The test file calls this keyword without needing to know the locator used for the calories input. Keeping the locator in the resource file means I only need to update one place when the page changes. This makes the test file easier to read and reduces repeated changes.

7. QP-01 must be a single Cypress test because QuickPizza uses a cookie to keep the browser connected to the same server, and the admin list only shows pizzas from that server. Cypress clears cookies before each test. If steps 6 and 7 were a separate test, the browser could connect to another server and the pizza created in steps 1 to 5 might not appear in the admin list. Keeping all seven steps in one test preserves the same browser session and server.
