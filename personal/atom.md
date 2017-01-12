# Atom

Settings: `⌘ + ,`

![](/assets/Skærmbillede 2017-01-12 kl. 12.38.12.png)

![](/assets/Skærmbillede 2017-01-12 kl. 12.39.15.png)

![](/assets/Skærmbillede 2017-01-12 kl. 12.44.07.png)

## Package: pigments

![](/assets/Skærmbillede 2017-01-12 kl. 12.50.09.png)

![](/assets/Skærmbillede 2017-01-12 kl. 12.51.08.png)

![](/assets/jan.-12-2017 13-10-44.gif)

## Package: minimap

![](/assets/Skærmbillede 2017-01-12 kl. 12.57.32.png)

![](/assets/Skærmbillede 2017-01-12 kl. 13.07.48.png)

## Package: atom-beautify

![](/assets/Skærmbillede 2017-01-12 kl. 12.58.07.png)

## Styling

Open Stylesheet: `Atom > Stylesheet`

Open inspector: `⌘ + alt + i`

```css
atom-workspace,
atom-text-editor {
  font-family: "Operator Mono";
  font-size: 11px;
  font-weight: 400;
  line-height: 1.7;
}
atom-panel.tool-panel {
  font-size: 0.88em;
}
.entity.other.attribute-name {
  font-style: italic;
}
atom-text-editor::shadow{
  .entity.other.attribute-name {
    font-style: italic;
  }
  .comment {
    font-style: italic;
  }
}

atom-text-editor.editor pigments-markers::shadow pigments-color-marker.syntax--dot, atom-text-editor pigments-markers::shadow pigments-color-marker.dot, atom-text-editor.editor pigments-markers::shadow pigments-color-marker.syntax--dot, atom-text-editor pigments-markers::shadow pigments-color-marker.dot, atom-text-editor.editor pigments-color-marker.syntax--dot, atom-text-editor pigments-color-marker.dot {
  transform: translate(0%, -50%) scale(0.8);
}
```





