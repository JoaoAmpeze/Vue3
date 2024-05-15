<template>
  <v-card theme="dark">
    <v-layout>
      <v-navigation-drawer
        expand-on-hover
        rail
      >
        <v-list>
          <v-list-item
            prepend-avatar="https://media.licdn.com/dms/image/D4E03AQFFHxqTCORPTg/profile-displayphoto-shrink_200_200/0/1677238200431?e=2147483647&v=beta&t=tNRJ2G0BiO_6QNS0iHVfIMUK-vR-J0hlwX7CE_H48Kw"
            subtitle="joaoampeze17@gmail.com"
            title="João Ampeze"
          ></v-list-item>
        </v-list>

        <v-divider></v-divider>

        <v-list density="compact" nav>
          <v-list-item prepend-icon="mdi-home" to="/" title="Home" value="h"></v-list-item>
          <v-list-item prepend-icon="mdi-folder" title="Meus Documento" value="myfiles"></v-list-item>
          <v-list-item prepend-icon="mdi-account-multiple" title="Compartilhar" value="shared"></v-list-item>
          <v-list-item prepend-icon="mdi-star" title="Favoritos" value="starred"></v-list-item>
          <v-list-item prepend-icon="mdi-twitter" to="/x" title="Twiter" value="x"></v-list-item>
          <v-list-item prepend-icon="mdi-table" to="/table" title="Tabela" value="t"></v-list-item>
          <v-list-item prepend-icon="mdi-table" to="/tabelaeditavel" title="Tabela Editavel" value="te"></v-list-item>
        </v-list>
      </v-navigation-drawer>

      <v-main style="height: 100vh background-color: black ">
      <slot/>
      
      </v-main>

      
    </v-layout>
  </v-card>
</template>

<script>
export default {
  name: 'default',
}
</script>