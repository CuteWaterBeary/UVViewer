# UV Viewer for Unity Editor
UVViewerWindow is an editor window extension class that allows you to view the UV of a mesh in the Unity Editor. Requires Unity version 5.4 or later.

![](Screenshot.png)

## Install
After downloading and importing the Unity package from our [release page](https://github.com/songkyoo/UVViewer/releases) or copying the [Assets/Plugins] folder into your project, UV Viewer will be added to the Window item in the menu bar. Running that item will create an editor window.

## Usage
### Mesh Settings
If the Mesh item is Selected Object, it will display UVs when a mesh or GameObject containing MeshFilter or SkinnedMeshRenderer components is selected.

If the Mesh item is set to Custom, you can set the mesh yourself. Dragging and dropping objects into the view area performs the same behavior. Draggable objects are meshes or GameObjects that contain MeshFilter or SkinnedMeshRenderer components.

### Setting the Texture
If the Mesh item is Selected Object and the selected game object contains MeshRenderer and SkinnedMeshRenderer components, you can select the texture of the materials included in the renderer if the Texture item is set to Materials.

If you set the Texture item to Custom, you can set your own texture. Dragging and dropping a texture into the view area performs the same behavior.

### Accessing from the Editor Script
You can set up the mesh or texture you created in the Editor Script. The following code sets the values in the window that is being displayed, if any, and creates a new window and sets the values if no window is being displayed.

```csharp
using Macaron.UVViewer.Editor;

class EditorClass
{
    void SetCustom(Mesh mesh, Texture texture)
    {
        // Mesh settings.
        UVViewerWindow.ShowWindow().SetCustomMesh(mesh);

        // Texture settings.
        UVViewerWindow.ShowWindow().SetCustomTexture(texture);
    }
}
```

Calling the `SetCustomMesh`, `SetCustomTexture` methods will change the Mesh, Texture items to Custom and set the Source to the value you called. Each method can be called individually.

## Limitations
1. the displayed UVs and textures do not automatically reflect changes made to the Source. If they need to be updated, they must be reloaded by pressing the Reload button on the Mesh, Texture item.

2. If the Geometry shader is not supported, the Line Thickness item is not available, and the view area is displayed in low resolution in HiDPI environments.
