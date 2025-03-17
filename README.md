<div><br/>

  <p align="center">
    <h2 align="center">Soho Okna - Website development and other IT services</h2>
    
</div>

**Soho Okna** is a small company I have been working with since the end of July. Our collaboration consisted of general IT services (e.g., domain and e-mail configuration), graphic designs (which can be seen below as well), and website development. There are plans to create a CMS server but at the momemnt, the website is just static site made with **React**.

<br>

You can see the current state of the development <a href="https://sohooknatesting.onrender.com">right here</a>.

At the moment <a href="https://soho-okna.pl">soho-okna.pl </a> contains only a placeholder page.

## About the website

I made all the necessary stuff required to host a functional static website with custom domain - from configuring the domain to managing hosting and deploying implemented website.

![HomePageDesktop]

Also the website is fully responsive both for desktops and mobile devices.


<p align="center">
    <img src="Images/SohoOknaDoorsMobile.png" alt="DoorsPageMobile">
</p>

## Project's structure and the React implementation

The project was developed using React framework, with scripts written in TypeScript. The project uses the MUI library for a nice looking components. To show how the project was implmeneted, there is an example below, showing how the door name is dynamically displayed, based on a chosen slide in a carousel. 

### Example scirpt - dynamic doors strings based on a type

- **DoorsTitles** - collection of door names, represented in a code as the dictionary, with a enum as a key, and an array of strings as a value
Doors section describing displayed door is consisted of three main eslements:
- **OfferingDoorsCarousel** - shows all of the door types as a carousel element
- **DoorsModelsSection** - displays Currently chosen slide (the middle one) has it's name displayed below. It also sets the _CurrentSlide_ state, based on the middle slide

``` ts
function DoorsModelsSection({currentSlide, chosenDoorsType, setCurrentSlide}:
 {currentSlide: number, chosenDoorsType: DoorsType, setCurrentSlide: React.Dispatch<React.SetStateAction<number>>}) 
{
    return(
        <>
            <OfferingDoorsCarousel 
                chosenDoorsType={chosenDoorsType} 
                setCurrentSlide={setCurrentSlide}
                />
            <Typography 
                color="#333333" 
                fontWeight={550} 
                fontSize={25} 
                alignSelf={'center'} 
                textAlign={'center'}
                >
                {DoorsTitles[chosenDoorsType][currentSlide]}
            </Typography>

            <DoorsDescriptionSection 
                currentSlide={currentSlide} 
                chosenDoorType={chosenDoorsType} 
                />
        </>
    );
}
```
The element _OffeeringDoorsCarousel_ uses the _react-slick_ implementing behaviour of the carousel. In the _Typography_ component, there is referenced a collection with door names based on a type. as an **Intrinsic Attribiute**.


#### The element below shows the states implementation and the 
``` ts
export default function OfferingDoorsSubpage()
{
    const [chosenDoorsType, setChosenDoorsType] = useState<DoorsType>(DoorsType.PVC);
    const [currentSlide, setCurrentSlide] = useState<number>(0);

    return(
        <Stack direction={'column'} width={'100%'}>
                    <SubSubPageTitle 
                    subPageName="Oferta" 
                    subSubPageName={"Drzwi"} 
                    bgImage={skyImage}
                    />

                <Box 
                    width={'85%'} 
                    maxWidth={'1600px'} 
                    alignSelf={'center'} 
                    mt={10} 
                    mb={10}
                    >
                    <Stack gap={5}>

                        {/* Drzwi zewnętrzne */}
                        <Box>
                            <ZewnetrzneDescSection/>
                            <DoorTypeButtonsSection 
                                chosenDoorsType={chosenDoorsType}
                                setChosenDoorsType={setChosenDoorsType} 
                                />
                            <BoxDivider/>
                        </Box>
                        <DoorsModelsSection 
                            currentSlide={currentSlide} 
                            chosenDoorsType={chosenDoorsType} 
                            setCurrentSlide={setCurrentSlide} 
                            />
                        
                        {/* Remeaining components */}

                    </Stack>
                </Box>

                <DoorsCatalogSection />
                <DoorsColorsSection />
        </Stack>
    );
}
```

## General IT service

Alongside the website aviable through the custom domain, I prepared the custom e-mail address as well (kontakt@soho-okna.pl). This required exposing the domain to the mailing service.

## Marketing materials

Additionally, I prepared all of the needed marketing materials, such us:

### Bussines card

<p align="center">
    <img src="Images/SohoOknaBussinessCardFront.png" alt="BussinesCard">
</p>

### Banner in a bigger format

<p align="center">
    <img src="Images/SohoOknaBanner.png" alt="Banner">
</p>

### Flyer

<p align="center">
    <img src="Images/SohoOknaFlyer.png" alt="Banner">
</p>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[HomePageDesktop]: Images/SohoOknaHomePageDesktop.png
[DoorsPageMobile]: Images/SohoOknaDoorsMobile.png
