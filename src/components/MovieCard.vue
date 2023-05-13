<template>
    <main>
      <div class="card mb-4 shadow-lg border border-secondary bg-dark text-light">
        <img
          class="card-img-top"
          :src="`${movie.poster.url}`"
          alt="Card image cap"
        />
        <div class="card-body overflow-auto"  style="height: 300px;">
          <p class="card-text">{{ movie.name }}</p>
          <div class="">
            <div class="d-flex justify-content-between align-items-center">
              <div class="btn-group">
                <button type="button" class="btn btn-sm btn-outline-secondary">
                  <i class="fas fa-heart"></i>
                </button>
                <button type="button" class="btn btn-sm btn-outline-secondary">
                  <i class="fas fa-plus"></i>
                </button>
              </div>
              <small class="ms-auto text-muted"
                >{{movie.description}}</small
              >
            </div>
          </div>
        </div>
      </div>
    </main>
  </template>

  <script>
  export default {
    name: "MovieCard",
    props: {
      movie: {
        type: Object,
        required: true,
      },
    },
  };
  </script>