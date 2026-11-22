# UI lab results

Tool parts that I chose: (ยังไม่เลือก)

## Part 0
- Step 0.1, Chrome version: 158.0.8127.37
- Step 0.3, ChromeDriver version: 158.0.8127.36
- Step 0.4, locator of Pizza, Please!: //button[normalize-space()='Pizza, Please!']
- Step 0.4, locator of Excluded tools: select[multiple]
- Step 0.4, locator of Must be vegetarian: //label[normalize-space()='Must be vegetarian']/preceding-sibling::input
- Step 0.4, locator of Custom Pizza Name: input#pizza-name
- Step 0.5, pizza name, tool and calories of the run by hand: Lab Pizza 20261122-212759, Pizza cutter, 550

| Step | Actual result | Pass or fail |
|------|---------------|--------------|
| 1    | The heading Looking to break out of your pizza routine? was shown | Pass |
| 2    | Max Calories per Slice, Excluded tools, Must be vegetarian and Custom Pizza Name appeared | Pass |
| 3    | Fields held 600, Knife excluded, vegetarian ticked and the name Lab Pizza 20261122-212759 | Pass |
| 4    | Answer showed the name Lab Pizza 20261122-212759, tool Pizza cutter and 550 calories per slice | Pass |
| 5    | The page said Please log in first. | Pass |
| 6    | After signing in as admin, the page showed Latest pizza recommendations | Pass |
| 7    | The list had the line Lab Pizza 20261122-212759 (tool=Pizza cutter, ingredients_number=6), the same tool as in step 4 | Pass |