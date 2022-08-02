# What is the requirement of pnpm?

Often software applications evolve so the engineering teams. We should be designing the application architecture in such a way that the engineering teams will be able to work on different sections of the software without much dependency. One such architecture is microservices(Yes micro-frontends with module federation in FE world).  

In such projects, we generally used to maintain the common dependencies in every section of project which caused memory issue. Instead, **pnpm** gives us an advantage to maintain the common dependcies between multiple projects in a **content-addressable-store** and uses **soft linking(like windows shortcuts) and hard linking(though it appears as its taking extra space on disk, it won't actually.)** to manage them in each section of project.  

# What is pnpm?

**Pnpm (Performant npm)** is dependency manager like npm or yarn. But unlikely it is having more advantages compare to them.

# Benefits of pnpm

* Global **content-addressable-store** to save disk space which inturn boosts installation time.
* Creates **Non-Flat node_modules** which helps to prevent some sceurity issues.
* Leverages **soft linking and hard linking** to virtually create non-flat node_modules directory.
* Leverages **hashing** to improve **updation process of store**.  
  
# Content-addressable-store

