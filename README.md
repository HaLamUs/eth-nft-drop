# eth-nft-drop

## Intro 
This project is my REACTION to the video 

<div>
  <a href="https://www.youtube.com/watch?v=_siRFuLEgGQ"><img src="https://img.youtube.com/vi/_siRFuLEgGQ/0.jpg" alt="IMAGE ALT TEXT"></a>
</div>

## Detail 
### Tech stack 
- <a href="https://thirdweb.com/"> thirdweb </a>
- <a href="https://nextjs.org/"> Nextjs </a>
- <a href="https://tailwindcss.com/"> tailwindcss </a>

### Kick-start project
```
npm create-next-app -e with-tailwindcss my-project
```
### Project structure
- 🗂 Folder pages where all pages in your site placed
- 🌈 TailwindCSS allows you quickly applying CSS to components
  - Font
  - Text size
  - Color
- Nextjs 
  - Replace class component by function component
  
  ```js
   function Search() {
      return (
        <div> Search <div/>
      )
   }
   
   export default Search
  ```
  - Path 
    - Ex: localhost:3000/NFT/para-farm
    - Create folder NFT under pages folder then ```[id].tsx``` this mean wildcard
    - 
  - Flexbox
    - https://www.w3schools.com/css/css3_flexbox.asp
    ``` js
    <div className="flex h-screen flex-col lg:grid lg:grid-cols-10">
      {/* Left */}
      <div className="lg:col-span-4">
        <div> LEFT </div>
      </div>
    </div>
    ```
    
    ```lg:min-h-screen``` meaning on large screen the min height of component is the height of the screen
    
    ```lg:h-96 lg:w-72``` meaning on large screen (height, width) = (96, 72)
    
    If not large screen case, it will back to 'flex' mode, meaning it will layout at it's ease
    <br/> ⚠️ Flex it NOT Grid
    <br/>Flex: 1 dimensional layout. Grid: 2
    <br/>  https://www.geeksforgeeks.org/comparison-between-css-grid-css-flexbox/
    <br /> Fine to use both at the same component

---
## Author

This repo was developed by [@lamha](https://github.com/HaLamUs). 
Follow or connect with me on [my LinkedIn](https://www.linkedin.com/in/lamhacs). 

## License
