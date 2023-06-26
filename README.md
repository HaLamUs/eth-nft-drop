# eth-nft-drop

## Intro 
This project is my REACTION to the video ⬇️

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
    
    ``` <button className="px-4 py-2 lg:px-5 lg:py3"/> ``` meaning ONLY (5,3) in large screen, OTHER screens (small, medium) will be (4,2). 
    Same apply for ```flex``` (small, medium) large will go with ```grid```
    
    ```flex-1 flex-col``` 1 meaning get all the space
    
    If not large screen case, it will back to 'flex' mode, meaning it will layout at it's ease
    <br/> ⚠️ Flex it NOT Grid
      - Flex: 1 dimensional layout, will expand all items in 1 line then go to next line.
      - Grid: 2
    <br/>
    https://www.geeksforgeeks.org/comparison-between-css-grid-css-flexbox/
    <br/> Fine to use both at the same component
    
  - Thirdweb: Wrap your entire app (_app.tsx)
    ```js
    return(
     <ThirdwebProvider desiredChainId={ChainId.bsc}>
      <Component {...pageProps} />
     </ThirdwebProvider>
    )
    ``` 
    
    👍 Beside that, thirdweb provides NFT drop, which you can just upload the images and hit Deploy button
    Instead of ```1.png``` and ```1.json``` we can use bulk upload replace json files by .csv
    
  - 🖖 Vercel: 
    <br/ >https://vercel.com/
    <br/> You can deploy your FE for free, connecting thru github
  - 😲 Opensea test net 
   <br/> https://testnets.opensea.io/
  - 🔴 Server side rendering 
    <br/> This one for Google robot, we don't return components, we return the data in json format

  - 🔴 Typescript
    <br/> We need define the type to avoid warning
    ```js
    // typings.d.ts where you specify how object should look
    interface Image {
     asset: {
      url: string
     }
    }
    export interface Creator {
     _id: string
     name: string
     image: Image
     bio: string
    }
    
    export interface Collection {
     _id: string
     title: string
     creator: Creator
     address: string
    }
    
    // index.js 
    interface Props {
     collections: Collection[]
    }
    ```
    Typescript using interface to define type

## THE end 
I see no reason to use Sanity as content center (CMS). 🤷‍♂️

---
## Author

This repo was developed by [@lamha](https://github.com/HaLamUs). 
Follow or connect with me on [my LinkedIn](https://www.linkedin.com/in/lamhacs). 

## License
