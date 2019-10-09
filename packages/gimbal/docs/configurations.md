# Gimbal Configurations

Available configurations for `config` section of your gimbal config file.

The configuration will be splited by audit types:

- [size](#size)
- [heap-snapshot](#heap-snapshot)

## size

Sets thresholds for given paths.

- Type: Path[] `Path { path: directoryPath, size: thresholdSize }`

Example:

```yaml
config:
  size:
    - path: ./build/precache-*.js
      maxSize: 10 KB
    - path: ./build/static/js/[0-9]*.chunk.js
      maxSize: 1 MB
    - path: ./build/static/js/*.chunk.js
      maxSize: 1 MB
    - path: ./build/static/js/runtime*.js
      maxSize: 10 KB
    - path: ./build/index.html
      maxSize: 10 KB
    - path: ./build/favicon.ico
      maxSize: 10 KB
    - path: ./build/
      maxSize: 18 MB
```

## heap-snapshot

Heap snapshot threshold parameters configurations:

#### Documents

- Type: int
- Default value: 5

```yaml
config:
  heap-snapshot:
    threshold:
      Documents: 5
```

#### Frames

- Type: int
- Default value: 2

```yaml
config:
  heap-snapshot:
    threshold:
      Frames: 2
```

#### LayoutCount

- Type: int
- Default value: 5

```yaml
config:
  heap-snapshot:
    threshold:
      LayoutCount: 5
```

#### Nodes

- Type: int
- Default value: 75

```yaml
config:
  heap-snapshot:
    threshold:
      Nodes: 75
```

#### RecalcStyleCount

- Type: int
- Default value: 6

Example:

```yaml
config:
  heap-snapshot:
    threshold:
      RecalcStyleCount: 6
```


