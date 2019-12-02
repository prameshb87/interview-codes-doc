Run the following command in the project root directory to create a local instance of the app. 

```
docker-compose up
```

The docs should then be available at [http://localhost:4567](http://localhost:4567). 

### Development
[Slate](https://github.com/slatedocs/slate) uses [markdown](https://github.com/slatedocs/slate/wiki/Markdown-Syntax) to automatically build the documentation site. Edit the markdown in the `/source` folder to see the reflected changes in the generated site. 

### Deployment (GitHub pages)
1. Create a new development branch and make sure `./build` directory exists in the poject root folder.

2. Build a local static copy of the documentation site into the build directory by running the following in PowerShell within your development branch


```
docker run --rm -v $PWD/source:/usr/src/app/source -w /usr/src/app/source -v $PWD/build:/usr/src/app/build docs_app bundle exec middleman build --clean
```

3. The `/build` directory should now have the new code updates for the site. Copy, commit and push all of the files from the `build` folder from the development branch into the root of the `gh-pages` branch. This will *release* the changes to the site so that they now reflect on the Github Pages. 

4. Commit and push the development branch changes to Github and make sure to merge the new changes into the `master` branch. 
