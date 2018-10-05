Choose a directory

```bash
cd my_boussole_compiler_for_c2n-sass-a
```

Install boussole inside a virtualenv

```bash
python3 -m venv env
source env/bin/activate
pip install wheel
pip install boussole
```

Method 1:

```bash
cd submodules/c2n-sass-e/sass
boussole compile
```

This will create ../build/app.css and ../build/app.map. Note that two static links are required:

```bash
cd ../../static/e/assets/css
ln -s ../../../../submodules/c2n-sass-e/build/app.css
ln -s ../../../../submodules/c2n-sass-e/build/app.map
``` 

Method 2:

Make the links, after correct DJU_DIR setting

```bash
ln -s $DJU_DIR/dju/submodules/c2n-sass-e
ln -s $DJU_DIR/dju/submodules/emencia-c2n
ln -s $DJU_DIR/dju/submodules/foundation-sites
ln -s $DJU_DIR/dju/submodules/Sveetoy
```

Create a settings.json file

```js
{
    "SOURCES_PATH": "emencia-c2n/sass/scss",
    "LIBRARY_PATHS": [
        "foundation-sites/scss",
        "Sveetoy/sources/sass/sveetoy"
    ],
    "TARGET_PATH": "css",
    "OUTPUT_STYLES": "expanded",
    "SOURCE_COMMENTS": false,
    "SOURCE_MAP": false,
    "EXCLUDES": []
}
```

Create the css directory

```bash
mkdir css
```

Build app.css

```bash
boussole compile
```

Move app.css to this submodule

```bash
mv css/app.css c2n-sass-e/build/app.css
```

