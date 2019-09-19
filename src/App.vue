<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="row">
      <div class="col-dm-12 text-center">
        <div class="alert alert-info">
          Info: Click a quote to deleted it !
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import QuoteGrid from './components/QuoteGrid'
  import NewQuote from './components/NewQuote'
  import Header from './components/Header'

  export default {
    components: {
      appQuoteGrid: QuoteGrid,
      appNewQuote: NewQuote,
      appHeader: Header
    },
    data() {
      return {
        maxQuotes: 10,
        quotes: [
          'This is a quote'
        ]
      }
    },
    methods: {
      newQuote(quote) {
        if(this.quotes.length == this.maxQuotes){
          return alert('Maximum quotes achieved ! Please delete a quote !')
        }
        this.quotes.push(quote)
      },
      deleteQuote(index) {
        this.quotes.splice(index)
      }
    }
  }
</script>