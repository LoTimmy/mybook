![](https://mjml.io/assets/img/logo-small.png)


```console
shell> npm install mjml
shell> npm i -g mjml
shell> ./node_modules/.bin/mjml index.mjml
shell> mjml input.mjml -o my-email.html
```
```console
shell> mjml -r index.mjml
shell> mjml -r index.mjml -o index.html
shell> mjml --watch index.mjml index.html
```

```mjml
<mjml>
  <mj-body>
    <mj-container>
      <mj-section>
        <mj-column>

          <mj-image width="100" src="/assets/img/logo-small.png"></mj-image>

          <mj-divider border-color="#F45E43"></mj-divider>

          <mj-text font-size="20px" color="#F45E43" font-family="helvetica">Hello World</mj-text>

        </mj-column>
      </mj-section>
    </mj-container>
  </mj-body>
</mjml>
```


```mjml
<mjml>
  <mj-body>
    <mj-container>
      <mj-section>
        <mj-column>
          <mj-text>Hi sexy!</mj-text>
        </mj-column>
      </mj-section>
    </mj-container>
  </mj-body>
</mjml>
```

```mjml
<mjml>
  <mj-body>
    <mj-container>

      <!-- Company Header -->
      <mj-section background-color="#f0f0f0"></mj-section>

      <!-- Image Header -->
      <mj-section background-color="#f0f0f0"></mj-section>

      <!-- Introduction Text -->
      <mj-section background-color="#fafafa"></mj-section>

      <!-- 2 columns section -->
      <mj-section background-color="white"></mj-section>

      <!-- Icons -->
      <mj-section background-color="#fbfbfb"></mj-section>

      <!-- Social icons -->
      <mj-section background-color="#f0f0f0"></mj-section>

    </mj-container>
  </mj-body>
</mjml>
```



- https://mjml.io/try-it-live/templates/basic


#### :books: 參考網站：
- [Documentation](https://mjml.io/documentation)
