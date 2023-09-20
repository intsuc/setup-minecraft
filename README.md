# <samp>setup-minecraft</samp>

This action downloads and caches a specific version of Minecraft: Java Edition[^1].

## Inputs

### `version`

Minecraft version to use. Default `release`.

### `install`

Whether to install Minecraft. Default `true`.

### `cache`

Whether to cache Minecraft. Default `true`.

## Outputs

### `version`

Minecraft version used.

### `package`

Package used.

## Example usage

```yml
- uses: actions/checkout@v4
- id: minecraft
  uses: mcenv/setup-minecraft@v3
  with:
    version: "1.20.2"
- uses: actions/setup-java@v3
  with:
    distribution: "microsoft"
    java-version: ${{ fromJson(steps.minecraft.outputs.package).javaVersion.majorVersion }}
- run: |
    echo Running Minecraft ${{ steps.minecraft.outputs.version }}.
    echo "eula=true" > eula.txt
    java -jar $MINECRAFT nogui
```

[^1]: NOT OFFICIAL MINECRAFT PRODUCT. NOT APPROVED BY OR ASSOCIATED WITH MOJANG.
