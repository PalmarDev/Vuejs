<template>
  <div>
    <div class="card">
      <div class="card-header">
        <h4>
          Students
          <RouterLink class="btn btn-primary float-end" to="/students/create"
            >New Student</RouterLink
          >
        </h4>
      </div>
      <table class="table table-bordered">
        <thead>
          <tr>
            <th>First Name</th>
            <th>Last Name</th>
            <th>Gender</th>
            <th>Phone</th>
            <th>Email</th>
            <th>Birthdate</th>
            <th>Country</th>
            <th>City</th>
            <th>State</th>
            <th>Admission date</th>
            <th>Scholarship</th>
            <th>Culmination date</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="estudiante in estudiantes" :key="estudiante._id">
            <td>{{ estudiante.nombre }}</td>
            <td>{{ estudiante.apellido }}</td>
            <td>{{ estudiante.genero }}</td>
            <td>{{ estudiante.telefono }}</td>
            <td>{{ estudiante.correo }}</td>
            <td>{{ estudiante.fechaNacimiento }}</td>
            <td>{{ estudiante.pais }}</td>
            <td>{{ estudiante.ciudad }}</td>
            <td>{{ estudiante.estado }}</td>
            <td>{{ estudiante.fechaIngreso }}</td>
            <td>{{ estudiante.beca }}</td>
            <td>{{ estudiante.fechaCulminacion }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      estudiantes: [],
    };
  },
  mounted() {
    axios
      .get("https://lexpin.net/estudiante")
      .then((response) => {
        this.estudiantes = response.data;
        console.log(response.data);
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>
