# UI lab results
Tool parts that I chose: Part 1 (Selenium IDE) and Part 2 (Selenium WebDriver in Java)

## Part 0
- Step 0.1, Chrome version: 158.0.8127.36
- Step 0.3, ChromeDriver version: 158.0.8127.36
- Step 0.4, locator of Pizza, Please!: button[name='pizza-please']
- Step 0.4, locator of Excluded tools: select[multiple]
- Step 0.4, locator of Must be vegetarian: #default-checkbox
- Step 0.4, locator of Custom Pizza Name: input#pizza-name
- Step 0.5, pizza name, tool and calories of the run by hand:

| Step | Actual result | Pass or fail |
|------|---------------|--------------|
| 1 | The heading "Looking to break out of your pizza routine?" | Pass |
| 2 | Max Calories, Excluded tools, Must be vegetarian and Custom Pizza Name appear | Pass |
| 3 | The field show the values | Pass |
| 4 | Pizza name show, tool show scissor, calories lower than 600 | Pass |
| 5 | Show please login first | Pass |
| 6 | It show latest recommendations | Pass |
| 7 | The Pizza name show | Pass |

## Part 1: Selenium IDE
- Firefox version and Node.js version: 160.0.1 and v25.0.0
- Step 1.4, the line of the failed check and the line Tests: × Running test web form (1404 ms). Actual value 'Received!' did not match 'Received' during assertText:id=message:Received
- Step 1.5, target chosen for Submit, and why the recorded one was fragile: `xpath=//button[@type='submit']`. The recorded `css=.btn` is a styling class that other buttons can share, so the test could click the wrong one.
- Step 1.6, commands changed, added or deleted after recording: assert part and clicking to selecting the input label
- Step 1.6, the pizza names of run 1 and run 2, from the lines info: echo: Lab Pizza 20261124-211050 Lab Pizza 20261124-211125
- Step 1.6, the line Tests: of both runs: Run 1: `Tests: 2 passed, 2 total`, Run 2: `Tests: 2 passed, 2 total`
- Step 1.7, one line of QP01customerTest.java that needs rewriting, and why:

## Part 2: Selenium WebDriver in Java
- Step 2.4, the failure line for the wrong title: [ERROR]   FirstTest.webFormOpens:19 expected: <Web Form> but was: <Web form>
- Step 2.15, QP01Test run 1, result and time: Passed (Tests run: 1, Failures: 0), 9.360 s 
- Step 2.15, QP01Test run 2, result and time: Passed (Tests run: 1, Failures: 0), 9.393 s
- Step 2.20, full run 1, time and number of tests: 23.539 s, 5 tests (5 passed)
- Step 2.20, full run 2, time and number of tests: 20.752 s, 5 tests (5 passed)

## Part B
1. The three number boxes all have the same id, so the id finds 3 boxes, not one. That is why the test finds the box by its label. If each box had its own id, the test would be shorter and would not break when the label text changes.

2. It is a consistency check, because it compares two parts of the site with each other. The tool is random, so the test cannot know it before. It would find a bug where the admin page shows a different tool from the one I got.

3. The test could read the ingredients and check that there is no meat or fish, like Pepperoni. For that it needs a list of which ingredients are vegetarian. It would be easier if the page showed "Vegetarian: yes".

4. Both tools waited for the page before checking it, Selenium IDE with wait commands and Java with WebDriverWait. Selenium IDE was faster to start, but I had to fix many recorded steps by hand. Java needed more code, but its error messages were clearer and it saved screenshots.

5. I would choose Selenium WebDriver in Java. Page objects keep the locators in one place, so tests are easy to read and fix. Both full runs passed 5 of 5 tests, and the screenshots show what happened.

6. `css=.btn` is a style that many buttons can share, so the test may click the wrong button. `xpath=//button[@type='submit']` finds the button by what it does. So it still works when the page looks different.

7. In QP01Test, the locator is inside the test, so I must change it in the test itself. In QP01PageObjectTest, I only change it once in `HomePage.java`. Every test that uses the page is fixed at the same time.
