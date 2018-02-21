# Nuclex.Fonts.Content.TrueTypeImporter

This repository contains Nuclex.Fonts.Pipeline.TrueTypeImporter with few small changes to work with Visual Studio 2017. You'll need to use [Nuclex Framework](http://nuclexframework.codeplex.com/) (or anything based on it, assuming it includes Nuclex.Fonts, like [Nucletic Framework](https://github.com/illuminus86/NuclecticFramework)).

Things that I've changed:
*I've added x64 target (you'll need to use this unless you're using 32bit content pipeline tool)
*I've changed marshalString function inside clix.h (the part I changed is `>::Type<` and I changed it into `>::template Type<`)
*I have removed all occurances of using namespace std; (this caused several errors)

I have tested this with Visual Studio 2017 (15.5.7), MonoGame 3.6.0.1625 and Windows Home 10 (1709). It's building successfully. Vector fonts are working correctly, but I haven't tested sprite fonts as they weren't the reason why I made this project run.

If you're using MonoGame then you'll need to add references to MonoGame.Framework and MonoGame.Framework.Content.Pipeline by yourself. If you're using this with anything else then you are on your own.

All classes overriding ContentTypeWriter:
*In .cpp files you might need to change `System::String ^VectorFontCharacterWriter::GetRuntimeReader()` and `System::String ^VectorFontCharacterWriter::GetRuntimeType()` if you use a port of Nuclex Framework with different namespaces.
*In .h files, there's an error (don't worry, code compiles without any issues) when overriding `protected: virtual void Write()`.
