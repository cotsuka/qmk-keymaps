# qmk-keymaps
⌨️ qmk external userspace

## Instructions
### Compiling These Keymaps
1. Run the normal `qmk setup` procedure if you haven't already done so -- see [QMK Docs](https://docs.qmk.fm/#/newbs) for details.
1. Clone this repo.
1. `cd` into this repository's clone directory
1. Set global userspace path: `qmk config user.overlay_dir="$(realpath .)"` -- you MUST be located in the cloned userspace location for this to work correctly
    - This will be automatically detected if you've `cd`ed into your userspace repository, but the above makes your userspace available regardless of your shell location.
1. Compile normally: `qmk compile -kb your_keyboard -km your_keymap` or `make your_keyboard:your_keymap`
    - Alternatively, if you configured your build targets above, you can use `qmk userspace-compile` to build all of your userspace targets at once.

## Creating New Keymaps
1. Add a new keymap for your board using `qmk new-keymap`
    - This will create a new keymap in the `keyboards` directory, in the same location that would normally be used in the main QMK repository. For example, if you wanted to add a keymap for the Planck, it will be created in `keyboards/planck/keymaps/<your keymap name>`
    - You can also create a new keymap using `qmk new-keymap -kb <your_keyboard> -km <your_keymap>`
    - Alternatively, add your keymap manually by placing it in the location specified above.
    - `layouts/<layout name>/<your keymap name>/keymap.*` is also supported if you prefer the layout system
1. Add your keymap(s) to the build by running `qmk userspace-add -kb <your_keyboard> -km <your_keymap>`
    - This will automatically update your `qmk.json` file
    - Corresponding `qmk userspace-remove -kb <your_keyboard> -km <your_keymap>` will delete it
    - Listing the build targets can be done with `qmk userspace-list`
1. Commit your changes
