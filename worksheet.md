# Project Overview: WornOut

## Project Links

- [GitHub Repo]
- [Client-side link](https://wornout.netlify.app/)
- [API link](https://damp-peak-94577.herokuapp.com/users/1/items)

## Project Description

A wardrobe tracking app that allows you to track how often you wear all your clothing. Provides data on what clothing & accessories you wear the most, and which items you should get rid of because you never wear them.

## User Stories
|#| User needs |  Functionality |
|--| --- | --- |
| 1 | I want to select which clothes I wear on a given day | A component that shows the day and menu of items that can be selected |
| 2 | I want to add new items | A form that accepts description of clothing, category and image |
| 3 | I want to delete an item when I get rid of it | A delete button on each item of clothing |
| 4 | I want to see details of how much I wear an item | A summary of data on an individual item with image |
| 5 | I want to see a summary of my whole wardrobe| A data visualization of when items are worn|
| 6 | I want to see suggestions of which items to get rid of | A data visualization of which items are worn the least|
| 7 | I want to see suggestions of which items I like the best | A data visualization of which items are worn the most|
| 8 | I want to categorize my items baised on function | A form that accepts multiple use category (shirt and workout gear) |
| 9 | I want to see items by category | A route that shows all items in a category|

### Route Table

|User need #| URL | HTTP Verb | Action | Description |
|-| --- | --- | --- | -----|
|5| /user/:id/items | GET | index | Summary of whole wardrobe |
|2 & 8| /user/:id/items | POST | create | Add a new item |
|4| /user/:id/items/:id | GET | show | Summary of data on individual item |
|8| /user/:id/items/:id | PUT | update | Edit details of individual item |
|1| /user/:id/items/:id  | PUT | update | Add wear count |
|3| /user/:id/items/:id  | DELETE | destroy | Delete individual item|
|7| /user/:id/wear_count/:params | GET | show | Summary of items worn the most |
|6| /user/:id/wear_count/:params | GET | show | Summary of items worn the most  | GET | show | Summary of items worn the least |
|9| /user/:id/category/:params | GET | show | list of all items in category |

## API Structure

### Data Schemas
```
{
    id: integer
    Username : string
}

{
    id: integer
    user_id: foreign key
    img: string
    category: string
    style: string
    use: string
    color: string
    wear_count: integer 
    created_at: date
}
```
<details>
<summary>Category: </summary>
    - top
    - bottom
    - shoes
    - onepeice
    - accessory
    - coat
 </details>

<details>
<summary>Style: </summary>
 - Sweater
 - Sweatshirt
 - t-shirt
 - tank-top
 - button-up shirt
 - long-sleaved shirt
 - pants
 - leggings
 - sweatpants
 - shorts
 - skirt
 - dress
 - jumpsuit
 - overcoat
 - jacket
 - sneaker
 - bag
 - heels
 </details>

<details>
 <summary>Use: </summary>
  - Workout
  - Outdoor
  - Sleep/lounge
  - Everyday
  - Work
  - Specialty
</details>

<details>
<summary>Color </summary>
   - blue
   - black
   - grey
   - cream
   - white
   - pink
   - green
   - yellow
   - orange
   - brown
   - denim
   - metalic
   - multi
   - purple
</details>


## Architecture
[Architecture](https://res.cloudinary.com/dcvgmixhx/image/upload/v1614710835/WornOut/Architecture_fvnuvn.png)

## Wireframes

Mobile


Tablet


Desktop


## MVP/PostMVP 

#### MVP 
- All components
- All routes to satisfy user stories
- Heat map on individual items
- Worn Most and Worn Least queries
- Use svelte to create client side
- Onclick update route increasing wear count
- mobile, tablet, desktop responsive
- Slide out animation on buttons
- triangle turn animation on drop down
- API create with Ruby on Rails
- scroll section on main page


#### PostMVP
 - able to backdate wear data
 - Image uploader
 - Image editor
 - Add all of my clothes
 - user creation
 - user  authentication       


## Components 

| Component | Description | Page (Y/N) |
| --- | :---: | --- | 
| Main | Home page, current date, render nav, find, render Find and Worn component   | Y |
| Nav | links to add new, closet, about   | N |
| Find  | Search form with get route with query to see all items in category , scroll in component section only  | N | 
| Worn  | button to update wear count through update route | N | 
| Form  | Form to add new item or update current item | Y |
| Closet | Renders the worn most and worn least components and nav | Y | 
| All | Get all data with links to individual items | Y |  
| Item | Summary of data on one items w/ heat map and buttons to update, destroy, and mark as worn | Y |  
| WornMost | Renders query of data with highest wear count | N |  
| WornLeast | Renders query of data with lowest wear count | N |  
| Chart | heatmap of wear data for the month with option to scroll to other months | N | 



## Time Estimates

| Component | Priority | Estimated Time | Time Invetsted | Actual Time |
| --- | :---: |  :---: | :---: | :---: |
| Basic API w/ seed data | H | 1 hr| 4 | 4 |
| Customized REST routes | H | 1 hr| 3 | 4 |
| Query routes | H | 2 hr| - | - |
| Setting up component and route structure | H | 2 hr| 4 | 4 |
| Nav component | H | 2 hr| 2 | 2 |
| About component | H | 1 hr| - | - |
| Main component w/ current date| H | 2 hr| - | - |
| By category search component | H | 5 hr| - | - |
| Form to update route component | H | 3 hr| - | - |
| Closet component | H | 1 hr| 1 | 1 |
| Worn most get route w/ query component | H | 3 hr| - | - |
| Worn least get route w/ query component | H | 3 hr| - | - |
| Item component | H | 2 hr| 6 | 6 |
| Heat map component | H | 8 hr| - | - |
| Update button | H | 2 hr| 5 | 5 |
| Delete button | H | 1 hr| 5 | 5 |
| Styling | H | 16 hr| 10 | 10 |
| Research, Learning, Googling, Crying | H | |  | 25 |
|Total  |  | 61 hr|  | 66 |



## Additional Libraries
- Svelte
- Ruby on Rails
- pages.js

## Code Snippet

Updating the wear count by one

```//Catch dispatch from WoreIt handleClick and update wear count
const handleCount = (e) => {
	const { wear_count, id} = e.detail
	let updatedItem = {...item}
		 updatedItem.wear_count++

	//Put updated wear count data
	const addWearCount = async () => {
		const response = await fetch (url + `/${item.id}`, {
			method: "PUT",
			headers: {
				"Content-Type" : "application/json"
			},
			body: JSON.stringify(updatedItem)
		})
		if(response.ok){
			const result = await response.json()
			getOneItem(updatedItem.id)
		}
	}
	addWearCount()
}```