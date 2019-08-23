# Why this repo exists
I forked this project to reproduce an issue seen in the Atalasoft 11.1 line with Virtual Directories in IIS. 

# Modifications made by me
Added DocRootOutsideWeb folder containing Original and Saved subfolders
 - Original contains the default startup.pdf and tif. 
 - Saved is the save location

# Necessary config change to reproduce issue
After loading the solution in Visual Studio (2017 in my case), close VS and open the newly created IISExpress applicationhost.config file with a text editor. (Alternatively, you could deploy to a local IIS instance and add two virtual directories.)
 - Relative location .vs\config\applicationhost.config
 - Add two virtual directory entities to the Site as shown below. 
```XML
    <site name="Atalasoft.Demo.WebDocumentViewer" id="2">
        <application path="/" applicationPool="Clr4IntegratedAppPool">
            <virtualDirectory path="/" physicalPath="C:\PATH\TO\web-document-viewer-demo-fork\Atalasoft.Demo.WebDocumentViewer" />
            <virtualDirectory path="/Original" physicalPath="C:\PATH\TO\web-document-viewer-demo-fork\DocRootOutsideWeb\Original" />
            <virtualDirectory path="/Saved" physicalPath="C:\PATH\TO\web-document-viewer-demo-fork\DocRootOutsideWeb\Saved" />
        </application>
        <bindings>
            <binding protocol="http" bindingInformation="*:52958:localhost" />
        </bindings>
    </site> 
```
---
# Atalasoft DotImage Web Document Viewer demo
Demo application shows basic usage of Web Document Viewer component of [DotImage](https://www.atalasoft.com/Products/DotImage) product. Live verions of the demo is hosted on Azure: http://atalasoft-viewer-demo.azurewebsites.net/

![](https://atalasoft.visualstudio.com/_apis/public/build/definitions/789e0a22-6f04-4fac-91a5-ccc70df2a1f1/1/badge)

## Description

The Web Document Viewer is JavaScript based image viewing control that can be created on the client side and used to perform the following operations:

 - display single- and multi-page documents
 - show thumbnails for document pages
 - add/move/inserts new pages
 - work with annotations

Demo application demonstrates basic skeleton of Web Document Viewer-based application. With help of [DotImage NuGet Packages](https://www.nuget.org/profiles/Atalasoft) you may have local version of the demo running in mere minutes.

## Licensing
To run the demo locally, you need to have DotImage license. There are various way to acquire the license:

 - Use [DotImage Activation Wizard Visual Studio extension](https://visualstudiogallery.msdn.microsoft.com/88ff07c9-fe68-48bd-bfdc-3fbc8a0ec1db)
 - Download complete DotImage installation package from [Atalasoft web site](https://atalasoft.com). You will be prompted to activate the product during installation

## Related Articles

 - [Introducing NuGet Packages](http://atalasoft.github.io/2016/05/03/introducing-nuget/)
 - [Introducing Activation Wizard Extension](http://atalasoft.github.io/2016/05/14/introducing-activation-wizard-extension/) 
