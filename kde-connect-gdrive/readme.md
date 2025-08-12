# 📣 Instrucciones

Explicación:
: El sistema linux KDE, tiene problemas con la API de Google para conectarse a Google Drive
: Para ello reemplazamos el proveedor por la de GNOME

1. Previamente, asegúrate de tener instalado los complementos de KDE por terminal:

`sudo apt install kaccounts-providers`

`sudo apt install kio-gdrive `

2. Ubicamos la ruta:

`/usr/share/accounts/providers/kde`

3. Editar el archivo:

`google.provider`

4. Reemplazar este contenido:

```
<?xml version="1.0" encoding="UTF-8"?>
<provider id="google">
  <name>Google</name>
  
  <description>Gnome, Google Drive and YouTube</description>
  <icon>im-google</icon>
  <translations>kaccounts-providers</translations>
  <domains>.*google\.com</domains>

  <template>
    <group name="auth">
      <setting name="method">oauth2</setting>
      <setting name="mechanism">web_server</setting>
      <group name="oauth2">
        <group name="web_server">
          <setting name="Host">accounts.google.com</setting>
          <setting name="AuthPath">o/oauth2/auth?access_type=offline</setting>
          <setting name="TokenPath">o/oauth2/token</setting>
          <setting name="RedirectUri">http://localhost/oauth2callback</setting>
          
          <setting name="ResponseType">code</setting>
          <setting type="as" name="Scope">[
              'https://www.googleapis.com/auth/userinfo.email',
              'https://www.googleapis.com/auth/userinfo.profile',
              'https://www.googleapis.com/auth/calendar',
              'https://www.googleapis.com/auth/tasks',
              'https://www.googleapis.com/auth/drive'
          ]</setting>
          <setting type="as" name="AllowedSchemes">['https']</setting>
          <setting name="ClientId">44438659992-7kgjeitenc16ssihbtdjbgguch7ju55s.apps.googleusercontent.com</setting>
          <setting name="ClientSecret">-gMLuQyDiI0XrQS_vx_mhuYF</setting>
          <setting type="b" name="ForceClientAuthViaRequestBody">true</setting>
        </group>
      </group>
    </group>
  </template>
</provider>
```

5. Guardar como administrador
6. Realizar la conexión
