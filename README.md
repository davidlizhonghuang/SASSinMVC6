# SASSinMVC6

How to embed SASS in Visual Studio 2015

MVC 6 in vs2015 allows you to use SCSS file to create min.css via complieSASS embedded plugin. It means after you add a new scss file and code it, you can get a min.css automatically underneath. However, if you create this min.css in index.cshtml page, you will not get its css work for you. Because MVC 6 can only see the css file in wwwroot folder. Therefore, you need to use gulp js file to run task that can copied the min.css file from scss into site.min.css file in wwwroot. This site.min.css can be seen in index.cshtml.Therefore, no matter where you generate css file from scss file, gulp js task will move all of those to site.min.css via .pipe() method. So it is very easy for use to build up the scss file in vs2015. Please note that IT industry has come back to pick up SASS after LESS is implemented and its limitation is found.

CSS is becoming a key component in MVC6, messy css is not best practice. SASS is used to program css. VS2015 allow you to add scss file that can be compiled into css automatically by vs2015 compileSASS plugin. For example, we create a new folder scss and add a stylesheet.scss file as below After we put some css code in scss file and save it, Stylesheet.css file is generated automatically under its file via its map file.

Now we create a scss file somewhere, but its css file is not in wwwroot folder. How can we copy this css file into site.min.css automatically. We use gulp.js. After we create a MVC6 web application, gulpfile.js is created automatically , what we need to do is to add extra code in to complete my task as below

Create a new task in gulpfile,js
<pre>
gulp.task("min:scss", function () {
    return 
    gulp.src('./scss/StyleSheet.css')
        .pipe(concat(paths.concatCssDest))
       .pipe(cssmin())
       .pipe(gulp.dest('.'));

});

Run task as below

gulp.task("min", ["min:js", "min:css", "min:scss"]);

</pre>


Finally simply we add this link into index.cshtml which then can use the css from scss file for layout.

 

Summary
So it is very easy to use sass file in asp.net MVC6 web application 

