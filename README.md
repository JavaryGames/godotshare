GodotShare 
==========
This is a light version of the [godot share module](https://github.com/Shin-NiL/Godot-Share) for [Godot Game Engine](https://godotengine.org/) (2 & 3) for Android & iOS. You'll be able to share text and/or images in your apps.

How to use
----------

### Android
- Clone inside the "modules" directory on the Godot source.
- Recompile android export template following the [official instructions](http://docs.godotengine.org/en/latest/reference/compiling_for_android.html#compiling-export-templates).
In your project goto Export > Target > Android:
	- Options:
		- Custom Package:
			- place your apk from build
			
- Add the following lines to ```project.godot``` file (Godot 3) or ```engine.cfg``` (Godot 2):

```
	[android]
	modules="org/godotengine/godot/GodotShare"
```

If you have more separate by comma.

### iOS
- Clone inside the "modules" directory on the Godot source;
- Recompile the iOS export template following the [official instructions](http://docs.godotengine.org/en/stable/development/compiling/compiling_for_ios.html).
- For exporting, follow the [exporting to iOS official documentation](http://docs.godotengine.org/en/stable/learning/workflow/export/exporting_for_ios.html). 

#### Godot 2
Just make sure you're using your custom template (compiled in the previous step), for that  rename it to "godot_opt.iphone" and replace the file with same name inside the Xcode project.

#### Godot 3
- Export your project from Godot, it'll create an Xcode project;
- Copy the library (.a) you have compiled following the official documentation inside the exported Xcode project. You must override the 'your_project_name.a' file with this file.

API Reference (Android & iOS)
-------------

The following methods are available:
```python
# Share text
# @param String title
# @param String subject
# @param String text
shareText(title, subject, text)

# Share image
# @param String image_abs_path The image location absolute path
# @param String title
# @param String subject
# @param String text
void sharePic(image_abs_path, title, subject, text)
```

Usage
-------------
An important note is that the image you want to share must be saved on the ```"user://"``` virtual directory root to be accessible, you can use ```OS.get_user_data_dir()``` to get its absolute path (required by ```sharePic```).

In the demo directory you'll find a working sample project for Godot 2 and 3 where a screen capture is shared.

### Known Issues
The screen capture isn't working for the Godot 3 project, it's a known issue for mobile platforms and you can see more details [here](https://github.com/godotengine/godot/issues/16694).

