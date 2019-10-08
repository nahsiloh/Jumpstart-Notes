3rd sept 2019/ 4th sept 2019

https://thoughtworks-jumpstart.gitbook.io/book/front-end-web-development/css/css-basics

## CSS

- margin collapses for the same tagged item

- `box-sizing: border-box`

- `display: inline-block` works to adjust the height

- `margin-left:auto`

  `margin-right:auto`

  -  to center the text box within the page

- `text-align: center`

  - to center the text within the box



#### CSS positioning

https://www.w3schools.com/Css/css_positioning.asp

- **Static** = default position
- `position: relative`= element is positioned relative to the static position
- `postion: abosolute` = set from top right of the screen
- `postition: fixed` = image will follow while scrolling 
- `position: sticky` =  when the item is not at the top of the page 

Qn: to used fixed or sticky for navbars?

`z-index: 100` = for overlay/ stacking = does not work for static



#### CSS text

- **Single line ellipsis** = works on single line text 

  ```css
  overflow: hidden; white-space: nowrap; text-overflow: ellipses
  ```

- ##### Multiple line ellipsis

  ```css
  display: -webkit-box; -webkit-line-clamp: 3; -webkit-box-orient: vertical; overflow: hidden ;
  ```



#### CSS flexbox

- ##### flexbox

  - usually applied on the parent and will affect all the children

  ```css
  .flex{
      display: flex;
      flex-direction: row;
  }
  ```

- ##### Justify content

  - To adjust items vertically

  ```css
  .flex{
      display: flex;
      flex-direction: column;
      justify-content: space between
  }
  ```

  ###### Types of flex

  - justify-content: flex-start = default

  - justify-content: flex-end

  - justify-content: center

  - justify-content: space-around

  - justify-content: space between

    

- ##### Align items

  display: flex;

  align-items: center

- ##### Flex types

  - **Flex Grow** = applied to items within a flex container, affecting how the items are distributed within the space

  - ##### Flex Shrink




#### Font size

- `em`= takes reference to the parent font size

- `rem`= follows the root font size (preferable to use for font size)

  

#### Background colour

If you want to bleed a background, should put the background-colour in the root area.

```css
:root{
	background-color: black
}
```



#### CSS Grid

```css
// first create the grids

.resume{
    margin-left: auto;
    margin-right: auto; 
    max-width: 34em;
    border: 1px solid gray;
    padding: 1em;
    display:grid;
    grid-template-rows: auto;
    grid-template-columns: auto auto;
    // 3fr 2fr (fraction representation)
    grid-gap: 2em;
    grid-template-areas: 
        "name name"
        "address address"
        "experience skills"
        "experience education"
        "personal personal";
}

// then map the items to the grid template items
.resume-title{
    grid-row: name;
    grid-column: name;
    // to create a line
    border-bottom: 1px solid gray
}

@media only screen and (max-width:600px){
    .resume{
        grid-template-areas:
            "name"
        	"address"
            "skills"
        	"experience"
        	"education"
        	"personal";
}
    
```



#### BEM

block element modifier = method of naming css class 

eg `resume__info--personal`

__ = children of the parent

-- = more specific modifier

