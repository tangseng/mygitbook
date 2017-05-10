# gulp

gulp是工作任务/流程自动化构建工具。

**API：**
* gulp.src(globs[, options])
* gulp.dest(path[, options])
* gulp.task(name[, deps], fn)
* gulp.watch(glob[, opts], tasks)、gulp.watch(glob[, opts, cb])
* pipe (gulp.src操作后使用)
* gulp.run (被新版本废弃了)

**常用插件**
* gulp-uglify
* gulp-minify-css
* gulp-minify-html
* gulp-concat
* gulp-sass
* gulp-livereload

**相关文章**
* [Gulp中文网](http://www.gulpjs.com.cn/)