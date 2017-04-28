# vue-golden-layout
Integration of the golden-layout to Vue
## Installation


~~npm install --save vue-golden-layout~~
```
git clone...
```

## Example

```html
<layout-golden>
	<gl-col>
		<gl-component @resize="console.log('resize')" title="compA">
			<h1>CompA</h1>
		</gl-component>
		<gl-row>
			...
		</gl-row>
		<gl-stack>
			...
		</gl-stack>
	</gl-col>
</layout-golden>
```
## Usage
```javascript
import vgl from 'vue-golden-layout'
Vue.use(vgl);
```
The objects are differentiated into : The layout object (golden), the container objects (golden and glRow, glCol and glStack), the contained objects (glRow, glCol and glStack and glComponent).

### Control
The purpose has been to have it mainly behaving with Vue so :
- use v-if to add/remove an element
- v-for is supposed to work too but has not been tested

Properties like 'hidden' and 'title' are watched (but the 'hidden' property sucks)
#### CSS
The glComponent answers to this class to fit in the layout child container, that you can override
```stylus
.glComponent
	width 100%
	height 100%
	overflow auto
```
### Properties
#### glComponent
```typescript
title: string
```
#### Contained objects

```typescript
width: number
height: number
closable: boolean
hidden: boolean
```

### Events
#### Layout 
Straight forwards from golden-layout, refer to their doc
```javascript
itemCreated
stackCreated
rowCreated
tabCreated
columnCreated
componentCreated
selectionChanged
windowOpened
windowClosed
itemDestroyed
initialised
activeContentItemChanged
```
#### Contained objects
Straight forwards from golden-layout, refer to their doc
```javascript
show
shown
maximised
minimised
resize
hide
close
open
destroy
```
### Methods
#### Container
These are defined on the container objects

```javascript
addGlChild(child, comp)
```
'child' is a configuration object (cfr golden-layout doc.), 'comp' is a vue component of a contained object
The child.componentState.templateId will be managed : don't fuss with the IDs, just give the component (your specified ID won't be replaced)
```javascript
removeGlChild(index)
```
This function is called automatically on VueComponent.beforeDestroy
#### Contained objects
```javascript
hide()
show()
close()
```

