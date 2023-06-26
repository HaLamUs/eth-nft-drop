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

### Sketch
<img src="https://github.com/HaLamUs/eth-nft-drop/blob/main/assets/sketch.png">

🤓 Instead of editing in Mongo Atlas, we can use CMS for marketing team can edit too.

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
          <br/>Flex everything is on the same row
      - Grid: 2 dimensionals
          <br/>Split the screen by cols
    <br/>
    https://www.geeksforgeeks.org/comparison-between-css-grid-css-flexbox/
    <br/> Fine to use both at the same component which means depends on
  ```js
    // by row, but each row will divide by number of cols
      <flex>
        <grid />
      <flex/>
    // or 
    // by number of cols, but each col will layout in one row
      <grid>
        <flex />
      <grid/>
    ``` 
    
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

  - 🐸🐸🐸 Fetch
    - In ```Next.js``` using `getServerSideProps` to fetch data everytime it renders the page

      You should use getServerSideProps only if you need to render a page whose data must be fetched at request time
      https://nextjs.org/docs/pages/building-your-application/data-fetching/get-server-side-props
    
    - Next.js is server render/ pre-rendering
      <br/> *Actually*, both `React` and `Next.js` are hosted in Remote server so both are SSR (server side rendering) BUT
      react render page by download js files instead html tags like `Next.js` so Next is lil better

SSR | CSR
:--: | :--:
<img src="https://github.com/HaLamUs/eth-nft-drop/blob/main/assets/ssr.png" width="1200" /> | <img src="https://github.com/HaLamUs/eth-nft-drop/blob/main/assets/csr.png" width="1200" />


    https://www.freecodecamp.org/news/next-vs-react/
    https://blog.logrocket.com/create-react-app-vs-next-js-performance-differences/
    
- 🐸 Router
  ```js
  <Link href={/nft/collection.slug.current}>
    <div>
  </Link>
  ```
  `param?.id` for getting params in url
  
  https://nextjs.org/docs/pages/building-your-application/routing/linking-and-navigating

- 🐸  useEffect

  without `conditions` it will run every time it's render

```js
function NFTDropPage({collection}: Props) {
  const [claimedSupply, setClaimedSupply] = useState<number>(0)
  const nftDrop = useNFTDrop(collection.address)

  //🤌 CAN use many useEffect as you want 
  useEffect(()=> {
    //fetchPrice
  }, [])
  
  useEffect(()=> {
    if (!nftDrop) return; //defensive programming

    const fetchNFTDropData = async () => {
      const claimed = await nftDrop.getAllClaimed();

      setClaimedSupply(claimed.length)
    }
    fetchNFTDropData()
  },[nftDrop])
}
```


## THE end 
1. <del>I see no reason to use Sanity as content center (CMS). 🤷‍♂️
2. Surprisingly, this entire app despite strongly is a <b>Another blockchain tutorial<b>, but not a single line of Sol written.
thirdweb is all you need 🤔
3. Using testnet open-sea to check minting instead bsc-scan 👏

---
## Author

This repo was developed by [@lamha](https://github.com/HaLamUs). 
Follow or connect with me on [my LinkedIn](https://www.linkedin.com/in/lamhacs). 

## License
