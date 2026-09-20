# AI 3D Kit Lite

**Build and texture 3D models in chat.**

- No license - mod to your hearts desire.

Download the kit ZIP, attach it to a chat, and describe what to make. The assistant uses the included tools to create geometry, apply textures, inspect the result, and return a model you can download. You can start from a description, reference images, or a supported existing model.

## Start in ChatGPT

1. Download the kit ZIP from the repository's Releases section.
2. Drag the ZIP into a conversation on [chatgpt.com](https://chatgpt.com/) that supports accessible file uploads and Python execution.
3. Send the message below, followed by your model request.

> Open the attached AI 3D Kit ZIP. Read START_HERE.md and AGENTS.md, safely extract this copy, and run python kit.py boot. Use the kit to build the model I describe or reuse models and reference images I attach. Add appropriate textures, check hand placement when relevant, inspect actual model renders, and return a GLB, PNG previews, and an editable project ZIP. If I have not described a model yet, ask what I want to make.

The same message is in [CHATGPT_START.txt](CHATGPT_START.txt). You do not need to extract the ZIP on your computer or run the commands yourself when using a capable chat.

**Host requirement:** Uploading a ZIP does not execute it or add missing tools. The assistant runs a startup check first. Available upload types and execution tools depend on the chat and account; see [OpenAI's data-analysis documentation](https://help.openai.com/en/articles/8437071-data-analysis-with-chatgpt). Local use is also supported below.

## Things to try

> Make a low-poly wooden treasure chest with iron bands, worn edges, and a hinged-looking lid. Show the textured model and a clay view.

> Use these front, side, and rear images to build a weathered mechanical robot. Match the silhouette first, add textures, and check the palms, thumbs, and finger curl.

> Keep my uploaded GLB's geometry. Replace only the armor with chipped painted steel and give me the editable texture images too.

The assistant builds actual geometry. Reference images guide the design; they are not automatically reconstructed into a measured 3D object.

## Example made with the kit

![Actual kit render of the included procedural textured-prism example](docs/images/example.png)

This is a render of the exported GLB from [examples/textured_prism.json](examples/textured_prism.json), not generated concept art. Geometry and materials are procedural; no reference photograph or imported model is needed. [Example details](docs/ASSETS.md).

## What you receive

A finished project can include a self-contained **GLB with embedded textures**, actual PNG model previews, an offline HTML viewer, baked texture maps, and an editable recipe or task with its required assets. The assistant checks and packages those files into a project ZIP.

Save the project ZIP and kit ZIP. Upload both in another chat to continue from the saved recipe rather than rebuilding from memory. Detailed model projects stay separate so the reusable kit remains small.

## Included tools

| Workflow | Capabilities |
|---|---|
| Geometry | Primitives, chamfered prisms, curves, custom meshes, sculpt strokes, and geometry stamps. |
| Materials | Procedural surfaces, image textures, base color, normal, roughness, metallic, occlusion, emission, decals, and edge wear. |
| UVs | Existing/custom coordinates, metric tiling, and packed planar hard-surface charts. |
| Reuse | Supported static GLB import, node edits, assembly, and selected-node retexturing; optional OBJ/STL/PLY conversion. |
| Hands | Anatomical left/right, wrist anchors, palm direction, and exported-geometry checks for declared mechanical hands. |
| Review | CPU renders, clay/base-color/UV views, embedded-map extraction, texture checks, and artifact audits. |

## Local use

Use Python 3.11+ with NumPy, SciPy, Pillow, and jsonschema. Reuse compatible installed packages. In a local environment where packages are missing, install the specifications in [requirements.txt](requirements.txt); [requirements-import.txt](requirements-import.txt) additionally enables optional trimesh conversion.

Run from the extracted kit folder:

```bash
python -B kit.py boot
python -B kit.py build examples/textured_prism.json --out ../3d_work/example --size 640
python -B kit.py render ../3d_work/example/model.glb --out ../3d_work/review --review --aa 2
python -B kit.py textures ../3d_work/example/model.glb --out ../3d_work/maps
python -B kit.py audit ../3d_work/example --latest
python -B kit.py pack ../3d_work/example --out ../3d_work/example.zip
```

Use a new output folder for each changed build. No GPU, Blender installation, server, API key, or model-weight download is required for the built-in workflow. It operates offline once its dependencies are available; Python and the packages themselves are not bundled.

## Scope

The kit creates static models. It does not provide neural image-to-3D reconstruction, automatic photogrammetry, rigging, animation, a general Boolean solver, seamless organic UV unwrapping, or certified print-ready output. Hidden surfaces and dimensions are design assumptions unless supplied.

The offline viewer requires WebGL 2 for interactive orbit controls and offers still-image fallbacks. Previews use approximate lighting. Declared-hand checks do not automatically validate imported/custom hands; those need visual review. A successful audit does not certify resemblance or watertightness.

## Guides

[Quick start](START_HERE.md) · [Assistant instructions](AGENTS.md) · [Modeling](GUIDE.md) · [Textures](TEXTURES.md) · [Hands](HANDS.md) · [Architecture](docs/ARCHITECTURE.md)

[Changes](CHANGELOG.md) · [Contributing](CONTRIBUTING.md) · [Releasing](PUBLISHING.md) · [Security](SECURITY.md)

## License

The kit's code, documentation, and included procedural examples are available under the [MIT License](LICENSE). Third-party components retain their own licenses and credits; see [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md). Uploaded models and images keep their own terms.
