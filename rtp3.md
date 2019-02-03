## Relief Terrain Pack (RTP3) integration

Relief Terrain Pack v3 (aka RTP3) is a famous package of shaders on the Asset Store that offers high quality shaders for terrains. It includes a triplanar shader that is perfectly compatible with Ultimate Terrains.

Before using it, edit the file **ReliefTerrainPMTriplanarStandalone.shader** in ReliefPack/Shaders/ReliefTerrain/VertexControl in a text editor and comment the line **#define LOCAL_SPACE_UV** and the line **#define WNORMAL_COVERAGE_X_Z_Ypos_Yneg** (add "//" at the beginning of the line). Save it. The shader is now ready to be used with uTerrains.

Then, drag & drop ReliefTerrainVertexBlendTriplanar material (you will find it in the same folder than the shader) to the material field of your terrain (or you can add a new material if you want as uTerrains supports multiple materials).

Finally, be careful with your vertex colors: RTP uses colors differently than the shader that is included with uTerrains. First texture maps with red color (255, 0, 0, 0), second texture maps with green (0, 255, 0, 0), third texture maps with blue (0, 0, 255, 0) and fourth texture maps with alpha (0, 0, 0, 255). If needed, adjust the vertex color of your voxel types and you're done with RTP integration.
