<template>
    <div class="container">
        <app-bar-quote :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-bar-quote>
        <app-new-quote @quoteAdded="newQuotes"></app-new-quote>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">
                    Info: Click on a quote to delete it
                </div>

            </div>
        </div>
    </div>
</template>

<script>
import QuotesGrid from './QuotesGrid.vue'
import NewQuote from './NewQuote.vue';
import Header from './Header.vue';
    export default {
        data: function(){
            return{
                maxQuotes: 10,
                quotes:['This is the first quote']
            };
        },
        methods:{
            newQuotes(quote){
                if(this.quotes.length >= this.maxQuotes)
                {
                    return alert('Please Delete the quote first!')
                }
                this.quotes.push(quote);
                
            },
            deleteQuote(index){
                this.quotes.splice(index,1)
            }
        },
        components:{
            'app-quote-grid': QuotesGrid,
            'app-new-quote' : NewQuote,
            'app-bar-quote' : Header
        }
        
    }
</script>

<style>
</style>
