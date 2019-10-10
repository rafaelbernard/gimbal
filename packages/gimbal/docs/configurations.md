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

Heap snapshot threshold parameters configurations. All minimum default configurations and values aplied should look like:

```yaml
config:
  heap-snapshot:
    threshold:
      Documents: 5
      Frames: 2
      LayoutCount: 5
      Nodes: 75
      RecalcStyleCount: 6
```

The complete configuration should look like:

```yaml
configs:
  heap-snapshot:
    threshold:
      Documents: 5
      Frames: 2
      JSHeapTotalSize: 200000
      JSHeapUsedSize: 100000
      LayoutCount: 5
      Nodes: 75
      RecalcStyleCount: 4
```

#### Documents

Number of documents in the page.

- Type: number
- Default value: 5

```yaml
config:
  heap-snapshot:
    threshold:
      Documents: 5
```

#### Frames

Number of frames in the page.

- Type: number
- Default value: 2

```yaml
config:
  heap-snapshot:
    threshold:
      Frames: 2
```

#### LayoutCount

Total number of full or partial page layout.

- Type: number
- Default value: 5

```yaml
config:
  heap-snapshot:
    threshold:
      LayoutCount: 5
```

#### Nodes

Number of DOM nodes in the page.

- Type: number
- Default value: 75

```yaml
config:
  heap-snapshot:
    threshold:
      Nodes: 75
```

#### RecalcStyleCount

Total number of page style recalculations.

- Type: number
- Default value: 6

Example:

```yaml
config:
  heap-snapshot:
    threshold:
      RecalcStyleCount: 6
```

#### JSHeapTotalSize

Total JavaScript heap size.

- Type: number
- Default value: none

Example:

```yaml
config:
  heap-snapshot:
    threshold:
      JSHeapTotalSize: 200000
```

#### JSHeapUsedSize

Used JavaScript heap size.

- Type: number
- Default value: none

Example:

```yaml
config:
  heap-snapshot:
    threshold:
      JSHeapUsedSize: 100000
```


