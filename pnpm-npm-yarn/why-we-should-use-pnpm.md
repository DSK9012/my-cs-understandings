# **What is the requirement of pnpm?** 🤔

Often software applications evolve so the engineering teams. We should be designing the application architecture in such a way that the engineering teams will be able to work on different sections of the software without much dependency. One such architecture is microservices in BE and Micro-frontends with module federation in FE.  

In such projects, we generally used to maintain the common dependencies in every section of project which causes memory issue. Instead, [**pnpm**](https://pnpm.io/) gives us an advantage to maintain the common dependcies between multiple projects in a content-addressable-store and uses **Soft Linking and Hard Linking** to manage them in each section of project.  

# **What is pnpm?** 

**Pnpm (Performant npm)** is dependency manager like npm or yarn. But unlikely it is having more advantages compare to them. It saves disk space and boosts the installation speed.

**Best Resource:** [**Pnpm Docs**](https://pnpm.io/)

## **Benefits of pnpm**😍

* **Content addressable store**
* **Non-Flat node_modules**
* **Efficient Updation of store**.  
  
### **Content-addressable-store:**  
* Its a single placeholder for the all the dependencies of all projects/applications in your system.
* When installing any new packages in project, it will get stored here in content-addressable-store. And the same will be [hard linked](https://github.com/DSK9012/my-cs-understandings/blob/main/soft-and-hard-linking/soft-linking-and-hard-linking.md) to your project node_modules directory. 
* This allows us to share the same version dependencies across projects without consuming additonal space again. 
* And whenever the same version dependency is required for new projects, it won't install it again, instaed it will deliver the same by [hard linking](https://github.com/DSK9012/my-cs-understandings/blob/main/soft-and-hard-linking/soft-linking-and-hard-linking.md) it to the node_modules directory. So This will surely increase the installation of dependencies. Isn't it....🥰!  

### **Non-Flat node_modules:**
* When installing dependencies with npm or Yarn Classic, all packages are hoisted to the root of the modules directory. As a result, source code has access to dependencies that are not added as dependencies to the project, it may cause security issues security issues and confusion with the dependencies.
* By default, pnpm uses [soft linking](https://github.com/DSK9012/my-cs-understandings/blob/main/soft-and-hard-linking/soft-linking-and-hard-linking.md) to add only the direct dependencies of the project into the root of the modules directory.
* In Pnpm, all peer dependencies(it includes actual dependencies also, so the root ones are soft linked to here and from here it will [hard linked](https://github.com/DSK9012/my-cs-understandings/blob/main/soft-and-hard-linking/soft-linking-and-hard-linking.md) to content addressable store.) are hoisted to the 2nd level of node_modules under .pnpm directory.
![Non-Flat node_modules structure](./non-flat-node-modules-structure.jpg)  

### **Efficient updation of store:** 
* Pnpm uses [**Hashing**](URL) concept to efficiently update the dependencies in content addressable store.
* [**Hashing**](URL) is being in used many applications like Git, Webpack etc., to efficiently identify the content changes rather than the file name changes.
* So when we are updating the store, only the files that differ are added to the store. For instance, if a dependency has 100 files, and a new version has a change in only one of those files, pnpm update will only add 1 new file to the store, instead of cloning the entire dependency just for the singular change. Isn't this awesome....👏!

